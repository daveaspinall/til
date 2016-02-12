# Remove SVG width/height using SVGO

Using the `removeDimensions` plugin that ships with SVGO, you can remove the
width/height attributes on an SVG in the presence of `"viewBox"`.

To optimise an SVG and remove the width/height attributes, run:

    svgo ../path/to/your/file.svg --enable removeDimensions


To do the same on a whole directory, run:

    svgo -f ../path/to/your/folder/ --enable removeDimensions

or:

    svgo -f ../path/to/your/source/ -o ../path/to/your/destination/  --enable removeDimensions

To list all available plugins, run:

    svgo --show-plugins

[Source](https://github.com/svg/svgo)
