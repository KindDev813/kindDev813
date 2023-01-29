<h1 align="center"> Integrate Jpegoptim to FFmpeg Open Source 🔥 </h1> 
<h3 align="center"> Davit Veranyan</h3>

# Sections 📚

✔️ Clone and Use\
✔️ How to migrate jpegoptim to FFmpeg, step by step \
✔️ Contact me


# Clone and Use 📋

1. Clone 📚

    - Clone the FFmpeg open source repository into your local system using below command:
        ```bash
        git clone https://gitlab.com/Autokroma/Tests/ffmpeg_DavitV.git
        ```
    - Generate Makefile to build this project in your local using ./configure command:
        ```bash
        ~/FFmpeg# ./configure
        ```
    - Install Linux package for dev environment:
        ```bash
        sudo apt install gcc
        ```

        ```bash
        sudo apt install make
        ```

        ```bash
        sudo apt install yasm
        ```

        ```bash
        sudo apt install nasm
        ```

        ```bash
        sudo apt-get install libjpeg-dev
        ```

    - Build project using make command:
        ```bash
        ~/FFmpeg# make
        ```
2. Use 🏆

    - NAME
        ```bash
        ffmpeg -launch_jpegoptim - utility to optimize/compress JPEG/JFIF files.
        ```
    - SYNOPSIS
        ```bash
        ffmpeg -launch_jpegoptim [ options ] [ filenames ]
        ```
    - DESCRIPTION
        ```bash
       jpegoptim is used to optimize/compress jpeg files. Program supports lossless optimization, which is based on optimizing the Huffman tables. And so called "lossy" optimization  where in addition to optimizing Huffman tables user can specify upperlimit for image quality.

       NOTE!  By  default jpegoptim modifies the input files (if they are optimized), to preserve original files use option -d to specify alternate directory for saving the optimized files to.

       Only normal files are optimized (symbolic links and special files are skipped).  Also, any other hard links to the file being optimized (as created using link(2)) are unaffected.
        ```
    - OPTIONS
        ```bash
       Options offered by jpegoptim are the following:

       -d<path>, --dest=<path>
             Sets alternative destination directory where to save optimized files (default is  to
             overwrite  the  originals).  Please  note that unchanged files won't be added to the
             destination directory. This means if the source file can't be  compressed,  no  file
             will be created in the destination path.

       -f, --force
             Force optimization, even if the result would be larger than the original file.

       -h, --help
             Displays short usage information and exits.

       -m<quality>, --max=<quality>
             Sets the maximum image quality factor (disables lossless optimization mode, which is
             by default enabled). This option will reduce quality of those source files that were
             saved  using  higher  quality  setting.  While files that already have lower quality
             setting will be compressed using the lossless optimization method.

             Valid values for quality parameter are: 0 - 100

       -n, --noaction
             Don't really optimize files, just print results.

       -S<size>, --size=<size>
             Try to optimize file to given size (disables  lossless  optimization  mode).  Target
             size  is  specified  either  in kilobytes (1 - n) or as percentage (1% - 99%) of the
             original file size.

       -T<threshold>, --threshold=<threshold>
             Keep the file unchanged if the compression gain is lower than the threshold (%).

             Valid values for threshold are: 0 - 100

       -b, --csv
             Print progress info in CSV format.

       -o, --overwrite
             Overwrite target file even if it exists (when using -d option).

       -p, --preserve
             Preserve file modification times.

       -P, --preserve-perms
             Preserve file permissions (owner/group) by overwriting the original  file.  This  is
             slightly less safe than the default mode of operation (where new file is first saved
             as temporary file and then renamed over the original file).  In this mode  a  backup
             of the original file is made with .jpegoptim.bak extension, and this file is removed
             after the original file has been successfully replaced.  NOTE! if running  jpegoptim
             as  root  there  is  generally  no  need to use this option, as jpegoptim is able to
             preserve file permissions when run by root in default mode.

       -q, --quiet
             Quiet mode.

       -t, --totals
             Print totals after processing all files.

       -v, --verbose
             Enables verbose mode (positively chatty).

       --all-normal
             Force all output files to be non-progressive. Can be used to convert all input files
             to progressive JPEGs when used with --force option.

       --all-progressive
             Force  all  output  files to be progressive. Can be used to convert all normal (non-
             progressive) JPEGs input files to progressive when used with --force option.

       -s, --strip-all
             Strip  all  markers  from  output  file.  (NOTE!   by   default   only   Comment   &
             Exif/IPTC/PhotoShop/ICC/XMP markers are kept, everything else is discarded).  Output
             JPEG still likely will contains one or two markers (JFIF and Adobe APP14)  depending
             on  colorspace  used  in  the  image,  as these markers are generated by the libjpeg
             encoder automatically.

       --strip-none
             Preserve "all" markers in the image. This will leave all markers  untouched  in  the
             image,  except JFIF (APP0) and Adobe (APP14) markers as those get regenerated by the
             libjpeg library.

       --strip-com
             Strip Comment (COM) markers from output file.

       --strip-exif
             Strip EXIF markers from output file.

       --strip-iptc
             Strip IPTC / Adobe Photoshop (APP13) markers from output file.

       --strip-icc
             Strip ICC profiles from output file.

       --strip-xmp
             Strip XMP profiles from output file.

       --stdout
             Send output image to standard output. Note, if optimization  didn't  create  smaller
             file than the input file, then no output (image) is sent to standard output. (Option
             -f can be used to force output of image always, even  if  optimized  image  was  not
             smaller than input).

       --stdin
             Read  input  image from standard input. When this option is used then only one image
             is read from standard output. Any (other) input files specified on command line  are
             ignored.   Note,  if  input  file '-' is seen on command line then standard input is
             also assumed.

             Currently this option will explicitly enable -f option, thus output image is  always
             sent to standard output (even if no optimization was possible).

        ```
    - Sample Compress / Optimize images command lines.
        
        Visit this website to study jpegoptins: https://vitux.com/optimize-jpeg-jpg-images-in-ubuntu-with-jpegoptim/ 

        Try to optimize file to a given size (disables lossless optimization mode). Target size is specified either in kilobytes (1 – n) or as a percentage (1% – 99%) of the original file size. 
        This is how you can specify size in kbs for the resulting image: 
        ``` dash
        ./ffmpeg -launch_jpegoptim --size=[size-in-kb] input.jpg
        ```
        Here is how you can specify the compression percentage:
        ``` dash
        ./ffmpeg -launch_jpegoptim -m[percentage_in_numbers] input.jpg
        ```
        example:
        ``` dash
        root@test9:~/Davit/FFmpeg_completed# ./ffmpeg -launch_jpegoptim --size=16k input.jpg
        Jpegotim Called
        input.jpg 512x512 24bit N JFIF [OK] 55241 --> 17005 bytes (69.22%), optimized.
        ```

# How to migrate jpegoptim to FFmpeg, step by step ✏️

- Clone the FFmpeg open source repository into your local system using below command:
  ```bash
   git clone https://github.com/FFmpeg/FFmpeg.git
  ```
- After the successful clone of FFmpeg open source, clone the jpegoptim repository into FFmpeg dirctory using below command:
  ```bash
   git clone https://github.com/tjko/jpegoptim.git
  ```
- And rename jpegoptim dirctory to libjpegoptim.
  ```bash
   ~/FFmpeg/libjpegoptim
  ```

1. Edit FFmpeg main() func to intagrate jpegoptim's main() func:
    
    When you use the "ffmpeg -launch_jpegoptim ..." command line, this can connect to jpegoptim's main() func.
    ```javascript
    // FFmpeg/fftools/ffmpeg.c
    if (argc >= 2 && strcmp(argv[1], "-launch_jpegoptim") == 0 ){
            ...
        jpegoptim_main(argc-1, &argv[1]);
        return 0;
    }

    // include jpegoptim->main() func in fftools/ffmpeg.h
    #include "libjpegoptim/jpegoptim.h"
    ...
    ```
2. Edit jpegooptim's main() func name to jpegoptim_main() to connect to FFmpeg main():
    
    ```javascript
    // FFmpeg/libjpegoptim/jpegoptim.c
    int jpegoptim_main(int argc, char **argv)
    {
        ...
    }
    // FFmpeg/libjpegoptim/jpegoptim.h
    int jpegoptim_main(int argc, char **argv)
        ...
    ```
3. Delete jpegoptim origin Makefile and make a new Makefile with similar other libs Makefiles styles:

    ```javascript
    // FFmpeg/libjpegoptim/Makefile
    NAME = jpegoptim
    DESC = FFmpeg optimize/compress jpeg library

    HEADERS =   config.h                                                   \
                jpegmarker.h                                               \
	            getopt.h                                               	   \
	            jpegoptim.h							   \
	            version_major.h						   \

    OBJS =  jpegdest.o                                      \
            jpegsrc.o                           	        \
            jpegmarker.o                                    \
            misc.o                                          \
            jpegoptim.o                                     \

    CFLAGS = -g					        \
	        -DHAVE_CONFIG_H				\
	        -Wall					    \
	        -Wformat				    \
	        -Werror=format-security		\
    #LIBS = -lm				            \
	        -ljpeg				        \
    # Objects duplicated from other libraries for shared builds
    SHLIBOBJS                    += log2_tab.o
    ...
    ```
4.Make new version managemant files (version.c, version.h, version_major.h) in libjpegoptim diraectory.(#Refer to https://gitlab.com/Autokroma/Tests/ffmpeg_DavitV/-/tree/top/libjpegoptim)

5.To generate ffbuild/config.sh (It is important to match the jepg library url to in integrate libjpeg), You need to edit FFmpeg/Configure files(Many changes). (#Refer to https://gitlab.com/Autokroma/Tests/ffmpeg_DavitV/-/blob/top/configure)

6.To set jpeg library version & url, You need make libjpegoptim.pc, libjpegoptim.pc, libjpegoptim.version. (#Refer to https://gitlab.com/Autokroma/Tests/ffmpeg_DavitV/-/tree/top/libjpegoptim)

# Contact me ✨

    topdev02715@gmail.com
# kindDev0813
