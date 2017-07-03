# pdfstitch

`pdfstitch` does a similar job to `pdfnup` but incorporates the following additional features:

* Crop pages to a certain size
* Adjust the crop position per page

## Dependencies

`pdfstitch` makes use of the following Perl modules:

* File::Basename (part of perl base)
* PDF::API2
* YAML

On Debian, you can installed them with:

`# apt install libpdf-api2-perl libyaml-perl`

## Usage

1. Run `genmeta` on your input PDF like so:

   `./genmeta foobar.pdf`

   This will generate a YAML file called `foobar.pdf.stitch`. Edit this file according to the desired output.
2. Optional: Run `genpreview` on that YAML file like so:

   `./genpreview foobar.pdf.stitch`

   This will generate a new PDF called `foobar-preview.pdf` containing only the pages you selected
   in the YAML file with each page being overlayed with a transparent box showing the area the
   page will be cropped to.

3. Optional: Run `gencropped` on the YAML file. This will generate a new PDF called `foobar-cropped.pdf` containing
   only the pages you selected in the YAML file with each page being cropped as specified.
4. Run `pdfstitch` on the YAML file. This will generated a single-page PDF called `foobar-stitched.pdf` with all
   selected pages being as specified in the YAML file.

