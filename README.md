# PhpStorm URL Handler
forked from [
phpstorm-url-handler
](https://github.com/sanduhrs/phpstorm-url-handler).

This package contains a launcher to open files in PhpStorm at the defined line
number and an associated desktop file that conforms to the Desktop Entry
Specification for use in Gnome and KDE desktop environments.

## Installation

The executable `webstorm` or `wstorm` must be in your `$PATH`.
If it is not, either add the install location to your path

    export PATH="/path/to/webstorm/bin/webstorm.sh:$PATH"

or symlink it to one of `/usr/bin` or `/usr/local/bin` - which already should be in your `$PATH`.
Use `sudo` if needed

    ln -s /path/to/webstorm/bin/webstorm.sh /usr/bin/webstorm

If you are installing Webstorm from [JetBrains Toolbox](https://www.jetbrains.com/lp/toolbox/). you can create a new path and point it to the toolbox shell scripts location i.e 
```
export PATH="/home/$username/.local/share/JetBrains/Toolbox/scripts"
```


Then copy the actual handler to your `$PATH` and make it executable.
Use `sudo` if needed

    cp webstorm-url-handler /usr/bin/webstorm-url-handler
    chmod +x /usr/bin/webstorm-url-handler

Install the `.desktop` file to register the mime-types.
Use `sudo` if needed

    desktop-file-install webstorm-url-handler.desktop
    update-desktop-database

## Usage

It can be used to open files at the specified line from within the browser by 
placing a link of the following kind in the markup:

    <?php
    $file = "/path/to/filename.php";
    $line = 35;
    print "<a href='webstorm://open?url=file://$file&line=$line'>Open with webstorm</a>";
    // Alternate Syntax to match webstorm 8 for the Macintosh
    print "<a href='webstorm://open?file=$file&line=$line'>Open with webstorm</a>";
    ?>

## Command-line usage

    FILE="/path/to/filename.php"
    LINE=35
    ./webstorm-url-handler "webstorm://open?url=file://${FILE}&line=${LINE}"


This alternative syntax matches the format used by
webstorm 8 for the Macintosh for cross-platform compatibility.

    FILE="/path/to/filename.php"
    LINE=35
    ./webstorm-url-handler "webstorm://open?file=${FILE}&line=${LINE}"


## License

GNU GENERAL PUBLIC LICENSE
