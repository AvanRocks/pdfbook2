# pdfbook2 - transform pdf files to non-foldable booklets

Create neat-looking non-foldable booklets with custom margins and **crop out
unecessary whitespace**.

Note: By "non-foldable booklet", I mean a booklet-style format with 2 pages on
each side of paper, but usable without folding the papers into halves.

If you want to create regular "foldable" booklets, check out the upstream repo,
or the master branch on this repo.

Upstream:

    pdfbook2 v1.4 (https://github.com/jenom/pdfbook2)
    (c) 2015 - 2020 Johannes Neumann (http://www.neumannjo.de)
    licensed under GPLv3 (http://www.gnu.org/licenses/gpl-3.0)
    based on pdfbook by David Firth with help from Marco Pessotto
    
## DESCRIPTION

		Create print-ready PDF files from some INPUT PDF files for booklet-style
		printing, but without the need to fold the papers in half. Simply print the
		outputted pdf file, staple the top-left corner and flip through the pages
		as you would a normal stack of papers. The pages will be in order.

		The advantage of this is that you will not need to fold the paper (like a
		booklet), which is useful if your pdf has many pages and folding would be
		unfeasable. You also don't need a large stapler for this style of formatting.

		The resulting files need to be printed in landscape/long edge double sided
    printing. The default paper format depends on the locale and is choosen by
    pdfjam. It can be set with the --paper option. 
    
    Before the pdf is composed the INPUT file is **cropped** to the relevant area in
    order to discard unnecessary white spaces. In this process, all pages are
    cropped to the same dimensions. Extra margins can be defined at the edges of 
    the booklet and in the middle where the binding occurs.
    
    The OUTPUT is written to INPUT-book.pdf. Existing files will be overwritten.
    All input files are processed seperatly.

## LICENSE      
             
    This program is free software: you can redistribute it and/or modify it 
    under the terms of the GNU General Public License as published by the Free 
    Software Foundation, either version 3 of the License, or (at your option) 
    any later version.

    This program is distributed in the hope that it will be useful, but WITHOUT 
    ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or 
    FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for 
    more details. You should have received a copy of the GNU General Public 
    License along with this program. If not, see <http://www.gnu.org/licenses/>.
    
## INSTALLATION

    Simply copy the file to any convenient location preferably covered by the 
    PATH variable of your shell. Make sure it is set as executable like
        
        chmod +x pdfbook2
    
    for unix like systems.
    
## REQUIREMENTS

    python 3.6, pdfjam, pdfcrop and their dependencies.
    
## EXAMPLES

    To simply create a non-foldable booklet from input.pdf you can use
        
        pdfbook2 input.pdf
        
    to create input-book.pdf. To select a special type of paper you can do
        
        pdfbook2 --paper=letter input.pdf
    
    for letter or
        
        pdfbook2 --paper=a4paper input.pdf
        
    for standard A4. To increase the inner margin for binding use
    
        pdfbook2 --inner-margin=200 input.pdf
        
    to increase the default value of 150. You can submit multiple files to the 
    script for processing like
        
        pdfbook2 input1.pdf input2.pdf
        
    which will result in input1-book.pdf and input2-book.pdf.

		Use the -o, -i, -t, and -b options to control margins to your liking
		(See options below for more info)
    
## USAGE

    pdfbook2 [options] file1 [file2 ...]

## OPTIONS

    --version   show program's version number and exit
    --help, -h  show this help message and exit

    GENERAL

        --paper=STR, -p STR
                Format of the output paper dimensions as latex keyword (e.g.
                a4paper, letterpaper, legalpaper, ...)
        --short-edge, -s
                Format the booklet for short-edge double-sided printing
        --no-crop, -n
                Prevent the cropping to the content area

    MARGINS

        --outer-margin=INT, -o INT
                Defines the outer margin in the booklet (default: 40)
        --inner-margin=INT, -i INT
                Defines the inner margin between the pages in the booklet
                (default: 150)
        --top-margin=INT, -t INT
                Defines the top margin in the booklet (default: 30)
        --bottom-margin=INT, -b INT
                Defines the bottom margin in the booklet (default: 30)

    ADVANCED

        --signature=INT
                Define the signature for the booklet handed to pdfjam, needs to 
                be multiple of 4 (default: 4)
        --signature*=INT
                Same as --signature
        --resolution=INT
                Resolution used by ghostscript in bp (default: 72)
