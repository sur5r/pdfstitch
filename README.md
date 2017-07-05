# pdfstitch

`pdfstitch` does a similar job to `pdfnup` but focuses on the following features:

* Crop pages to a certain size
* Adjust the crop position per page

## License
`pdfstitch` is free software under the GNU AGPL version 3. See `LICENSE` for details.

## Dependencies

`pdfstitch` makes use of the following Perl modules:

* File::Basename (part of perl base)
* File::LibMagic
* Getopt::Long (part of perl base)
* PDF::API2
* YAML

On Debian, you can installed them with:

`# apt install libpdf-api2-perl libyaml-perl`

## Usage

1. Run `pdfstitch` on your input PDF:

   `./pdfstitch [--genmeta] foobar.pdf`

   This will generate a YAML file called `foobar.pdf.stitch`. Edit this file according to the desired output.
   This is also the default action if called with a PDF.
2. Optional: Generate a preview and/or cropped PDF:

   `./pdfstitch --preview foobar.pdf.stitch`

   This will generate a new PDF called `foobar-preview.pdf`.
   It contains only the pages you select in the YAML file with each page being overlayed with a transparent box
   showing the are the page will be cropped to.

   `./pdfstitch --crop foobar.pdf.stitch`

   This will generate a new PDF called `foobar-cropped.pdf`.
   It contains only the pages you select in the YAML file with each page being cropped accordingly.
4. Generate the final stitched PDF:

   `./pdfstitch --stitch foobar.pdf.stitch`

   This will generated a single-page PDF called `foobar-stitched.pdf` with all selected pages being
   stitched together as specified in the YAML file.
   This is also the default action if called with just a meta file.

## Notes

* The output file name is based on the .stitch file name.
* All output files are placed in the current working directory.
