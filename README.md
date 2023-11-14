# pdfstitch

`pdfstitch` does a similar job to `pdfnup` but focuses on the following features:

* Crop pages to a certain size
* Adjust the crop position per page

It has been created to print sewing patterns distributed as A4 or Letter PDFs on a large format printer
thus saving oneself the hassle of cutting and gluing individual pages.

## License
`pdfstitch` is free software under the GNU GPL version 3. See `LICENSE` for details.

## Dedication

`pdfstitch` is dedicated to the memory of Janka "marsi" Kuhfuß.

## Dependencies

`pdfstitch` makes use of the following Perl modules:

* File::Basename (part of perl base)
* File::LibMagic
* Getopt::Long (part of perl base)
* PDF::API2
* YAML

On Debian, you can install them with:

`# apt install libfile-libmagic-perl libpdf-api2-perl libyaml-perl`

On FreeBSD, you can install them with:

`# pkg install p5-File-LibMagic p5-PDF-API2 p5-YAML`

## Usage

1. Run `pdfstitch` on your input PDF:

   `./pdfstitch [--genmeta] [--defaultcrop=0.9] foobar.pdf`

   This will generate a YAML file called `foobar.pdf.stitch`. Edit this file according to the desired output.
   This is also the default action if called with a PDF. Per default 10% (factor 0.9) is applied as crop factor.
   You can adjust this value with the --defaultcrop parameter.

2. Optional: Generate a preview and/or cropped PDF:

   `./pdfstitch --preview foobar.pdf.stitch`

   This will generate a new PDF called `foobar-preview.pdf`.
   It contains only the pages you select in the YAML file with each page being overlayed with a transparent box
   showing the area the page will be cropped to.

   `./pdfstitch --crop foobar.pdf.stitch`

   This will generate a new PDF called `foobar-cropped.pdf`.
   It contains only the pages you select in the YAML file with each page being cropped accordingly.

3. Generate the final stitched PDF:

   `./pdfstitch --stitch foobar.pdf.stitch`

   This will generate a single-page PDF called `foobar-stitched.pdf` with all selected pages being
   stitched together as specified in the YAML file.
   This is also the default action if called with just a YAML file.

## Notes

* The output file name is based on the .stitch file name.
* All output files are placed in the current working directory.
