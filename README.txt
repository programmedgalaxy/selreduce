selreduce is an application implementing OpenCV 2.4.13 to blur low-contrast regions
of images for noise reduction. It includes features for scaling and
configuration of execution parameters.

It was built with Microsoft Visual Studio 2015 (toolset version v140). The project
may have to be reconfigured if you want to build under a different environment.

The project properties reference an environment variable "$(OpenCV2Path)" which points
to the directory containing the "opencv" folder from a fresh extract of the OpenCV
2.4.13 package. Modify your environment variables or the project property page
appropriately to allow Visual Studio to find the necessary files.

If runtime errors occur at startup, the program can't find the necessary .dlls needed
for OpenCV. Locate a copy of the files "opencv_core2413[d].dll", "opencv_highgui2413[d].dll",
and "opencv_imgproc2413[d].dll", and place them in the same directory as the compiled
executable. (Use the "d" versions for a Debug configuration, and the non-"d" versions for
Release. Also remember to match x86 to x86 and x64 to x64.)

selreduce is a CLI application, and can be incorporated into a batch file or
shell script for optimized automated workflow.

To use selreduce, open a command prompt/terminal window. While located in the
same folder as selreduce, attempt to run it without any parameters.

A usage instructions printout will display. For convenience, it is reprinted
here:

Usage: selreduce <image file> [-o file] [-r #] [-t 0-100] [-s #f] [-v]
<image file> = the filename of the image to effect.
[-o] = the filename of the file to output. Defaults to out_<image file>.ext
[-r] = the radius of the blur to apply. Default value is 5, must be odd
[-t] = the threshold of value difference between pixels required to perform blur in that region. Default value is 50, range 0-100
[-s] = factor to scale the image by. Default is 1 (no scaling applied)
[-v] = enables verbose console output

Only the input file is a required argument. You can specify what filename to
output to, as well as configure the parameters of the program's operation.

Additionally, specifying the -v flag will enable verbose output, which will
display all of the program's execution steps as they begin and complete. This
can show how long selreduce is taking to complete its operations.

As an example, say I wanted to heavily blur only the most similar parts of an
image called picture.jpg, and I wanted to export it to it worked.jpg. I
also want to use verbose logging.

I would therefore want a high -r value, and a low -t value. I could run:

selreduce picture.jpg -o "it worked.jpg" -r 25 -t 5 -v
