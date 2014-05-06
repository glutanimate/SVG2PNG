SVG2PNG
=======

## Description

Simple Nautilus script to convert SVG to PNG based on DPI or resolution. Other file managers with custom actions should be supported, too.

## Screenshot

![](https://raw.githubusercontent.com/Glutanimate/SVG2PNG/master/SVG2PNG.png)

## Documentation


    # NAME:         SVG2PNG
    # VERSION:      0.1
    # AUTHOR:       (c) 2014 Glutanimate (https://github.com/Glutanimate)
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
    # LICENSE:      GNU GPLv3 (http://www.gnu.de/documents/gpl-3.0.en.html)
    #
    # NOTICE:       THERE IS NO WARRANTY FOR THE PROGRAM, TO THE EXTENT PERMITTED BY APPLICABLE LAW. 
    #               EXCEPT WHEN OTHERWISE STATED IN WRITING THE COPYRIGHT HOLDERS AND/OR OTHER PARTIES 
    #               PROVIDE THE PROGRAM “AS IS” WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESSED OR 
    #               IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY 
    #               AND FITNESS FOR A PARTICULAR PURPOSE. THE ENTIRE RISK AS TO THE QUALITY AND 
    #               PERFORMANCE OF THE PROGRAM IS WITH YOU. SHOULD THE PROGRAM PROVE DEFECTIVE,
    #               YOU ASSUME THE COST OF ALL NECESSARY SERVICING, REPAIR OR CORRECTION.
    #
    #               IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW OR AGREED TO IN WRITING WILL ANY 
    #               COPYRIGHT HOLDER, OR ANY OTHER PARTY WHO MODIFIES AND/OR CONVEYS THE PROGRAM AS 
    #               PERMITTED ABOVE, BE LIABLE TO YOU FOR DAMAGES, INCLUDING ANY GENERAL, SPECIAL, 
    #               INCIDENTAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OR INABILITY TO USE 
    #               THE PROGRAM (INCLUDING BUT NOT LIMITED TO LOSS OF DATA OR DATA BEING RENDERED 
    #               INACCURATE OR LOSSES SUSTAINED BY YOU OR THIRD PARTIES OR A FAILURE OF THE 
    #               PROGRAM TO OPERATE WITH ANY OTHER PROGRAMS), EVEN IF SUCH HOLDER OR OTHER 
    #               PARTY HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.
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

More documentation may be found [here](http://askubuntu.com/a/412583/81372).
