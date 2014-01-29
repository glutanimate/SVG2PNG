SVG2PNG
=======

## Description

Simple Nautilus script to convert SVG to PNG based on DPI or resolution. Other file managers with custom actions should be supported, too.

## Screenshot

![](http://i.stack.imgur.com/CIIRl.png)

## Documentation


    NAME:         SVG2PNG
    VERSION:      0.1
    AUTHOR:       (c) 2014 Glutanimate
    
    DESCRIPTION:  Simple application to convert SVG files to PNG files based on DPI or resolution. 
                  Designed to work as a context menu script in file managers like Nautilus and Thunar.
                  
    FEATURES:     - Converts SVG image file to PNG raster of a specific DPI or width
                  - SVG preview
                  - choose between converting the full SVG page or only the cropped image
                  
    DEPENDENCIES: inkscape imagemagick yad
                  YAD (1) is an advanced for of Zenity with many improvements. It's not included in the
                  official Ubuntu repos yet (2) but can be installed from a webupd8 PPA (3)
                  
    LICENSE:      MIT license (http://opensource.org/licenses/MIT)
    
    NOTICE:       THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
                  INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
                  PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
                  LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, 
                  TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE 
                  OR OTHER DEALINGS IN THE SOFTWARE.
                  
                  
    USAGE:        SVG2PNG image1.svg image2.svg [..]
                  I recommend installing this script as a context menu action for your file manager.
                  Instructions for Nautilus may be found on AskUbuntu (4).
                  
    NOTES:        The script uses convert for previews because it's faster. For optimal results
                  the actual conversion is done with inkscape's command line interface.
                  
    LINKS:        (1) https://code.google.com/p/yad/
                  (2) https://bugs.launchpad.net/ubuntu/+bug/796633
                  (3) https://launchpad.net/~webupd8team/+archive/y-ppa-manager
                  (4) http://askubuntu.com/questions/236414/how-can-i-install-a-nautilus-script

More documentation may be found [here](http://askubuntu.com/a/412583/81372).
