#salt_pepper.py

This script cleans an image with salt and pepper noise (ie: text dotted due to
bad pixel definition).

Transforms the image into gray-scale and applies a Gaussian Blur + a Median Blur
to get extra definition to the text. After getting extra pixels for the letters,
we use the function erode to outline the text in order to improve the quality of
the data read by OCR.

In the end, it applies a series of threshold values (or the ones received by
parameter) to the modified image and shows them one by one asking the user to
save the current threshold image.


###Common arguments

These are some of the main arguments used in this module:

    - input_file: input file, can be a file path or an image (np array).
    - thresh_val: limit value to apply threshold.
    - quality: quality to use in the pdf_to_png transformation.
    - window_size: size of the window used to blur. As this values increases so
                    does the blur.
    - kernel_size: size of the kernel used to blur. As this values increases so
                    does the blur.


###Import

To import this module into your application, you must include the following
line at the beginning of your own python file:

        import salt_pepper as sp


###Functions

In this section you'll find a summary of each function included in this module
except the *check_argument* functions, which always return either 0 or an
exception if any parameter is out of it's limits.


- ####clean(input_file,  thresh_val=200, window_size=5, kernel_size=5)

    Transforms the image into gray-scale and applies a Gaussian Blur + a Median Blur
to get extra definition to the text. After getting extra pixels for the letters,
we use the function erode to outline the text in order to improve the quality of
the data read by OCR.

    In the end, it applies each thresh_val to the image to get different versions of
the threshold source image.

    Returns: the input image with the previously described operations.


###Examples

In this case, we'll use an image with a lot of white noise:

![salt-pepper](../../resources/saltpepper.png)

The result obtained after aplying *clean()* is:

![salt-pepper-output](../../resources/saltpepper-output.png)

Note: tested with Tesseract, the upper image isn't readable, as the cleaned one is read perfectly.
