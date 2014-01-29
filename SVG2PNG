#!/bin/bash

# NAME:         SVG2PNG
# VERSION:      0.1
# AUTHOR:       (c) 2014 Glutanimate
#
# DESCRIPTION:  Simple application to convert SVG files to PNG files based on DPI or resolution. 
#               Designed to work as a context menu script in file managers like Nautilus and Thunar.
#
# FEATURES:     - Converts SVG image file to PNG raster of a specific DPI or width
#               - SVG preview
#               - choose between converting the full SVG page or only the cropped image
#
# DEPENDENCIES: inkscape imagemagick yad
#               YAD (1) is an advanced for of Zenity with many improvements. It's not included in the
#               official Ubuntu repos yet (2) but can be installed from a webupd8 PPA (3)
#
# LICENSE:      MIT license (http://opensource.org/licenses/MIT)
#
# NOTICE:       THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
#               INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
#               PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
#               LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, 
#               TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE 
#               OR OTHER DEALINGS IN THE SOFTWARE.
#
#
# USAGE:        SVG2PNG image1.svg image2.svg [..]
#               I recommend installing this script as a context menu action for your file manager.
#               Instructions for Nautilus may be found on AskUbuntu (4).
#
# NOTES:        The script uses convert for previews because it's faster. For optimal results
#               the actual conversion is done with inkscape's command line interface.
#
# LINKS:        (1) https://code.google.com/p/yad/
#               (2) https://bugs.launchpad.net/ubuntu/+bug/796633
#               (3) https://launchpad.net/~webupd8team/+archive/y-ppa-manager
#               (4) http://askubuntu.com/questions/236414/how-can-i-install-a-nautilus-script

############## DIALOGS ###################

TITLE="SVG to PNG"
ICON="svg"

############## USGCHECKS #################

# checks if user selected an item

if [ $# -eq 0 ]
  then
      yad --title="$TITLE" \
          --image=dialog-error \
          --window-icon=dialog-error \
          --class="$WMCLASS" \
          --text="Error: no file selected" \
          --button="Ok":0
      echo "Error: no file selected"
      exit
fi

############### GLOBVAR ##################

SVGFILES="$@"
TEMPDIR=$(mktemp -d)
PREVIEWIMG="$TEMPDIR/svgpreview.png"

############### CLEANUP ##################

trap "rm -r $TEMPDIR" EXIT 

############## FUNCTIONS #################

converttosvg_dpi(){

echo "Converting based on DPI."

while [ $# -gt 0 ]; do

    echo "$# file(s) left to convert."
    SVGFILE="$1"
    FILESTEM="${SVGFILE%%.*}"
    PNGFILE="$FILESTEM".png
    inkscape "$SVGFILE" -z --export-dpi="$DPI" \
    --"$AREASETTING" --export-png="$PNGFILE"
    shift
    
done
echo "Done."

}

converttosvg_res(){

echo "Converting based on Width."

while [ $# -gt 0 ]; do

    echo "$# file(s) left to convert."
    SVGFILE="$1"
    FILESTEM="${SVGFILE%%.*}"
    PNGFILE="$FILESTEM".png
    inkscape "$SVGFILE" -z --export-width="$WIDTH" \
    --"$AREASETTING" --export-png="$PNGFILE"
    shift
    
done
echo "Done."

}

createpreview() {
convert -resize 128x "$1" "$PREVIEWIMG"
}

getsettings() {

SETTINGS=$(yad --window-icon "$ICON" --image "$PREVIEWIMG" --width 300 --height 200 --always-print-result \
--form --separator="|" --title="$TITLE" --text "Please choose the DPI or resolution to convert to." \
--field="DPI:NUM" 10[!80..600[!10]] --field="Width in px:NUM" 16[!16..4096[!16]] \
--field="Area:":CB "Drawing"\!"Page" \
--button="Convert based on DPI:2" --button="Convert based on Resolution:3" --button="gtk-cancel:1")

RET=$? # Exit code?

if [ "$RET" = 252 ] || [ "$RET" = 1 ]  # WM-Close or "Abort"
  then
      echo "Exiting..."
      exit
fi

DPI=$(printf %.0f $(cut -d "|" -f 1 <<<"$SETTINGS")) #round values
WIDTH=$(printf %.0f $(cut -d "|" -f 2 <<<"$SETTINGS"))
AREA=$(cut -d "|" -f 3 <<<"$SETTINGS")

case "$AREA" in

Drawing)
  AREASETTING="export-area-drawing"
  ;;
  
Page)
  AREASETTING="export-area-page"
  ;;
  
esac

echo "DPI set to $DPI"
echo "Width set to $WIDTH"
echo "Area set to $AREA"

}


################ MAIN ####################

createpreview "$1"
getsettings

case "$RET" in

2)
  echo 2
  converttosvg_dpi "$@"
  ;;

3)
  echo 3
  converttosvg_res "$@"
  ;;
  
esac

exit 0
