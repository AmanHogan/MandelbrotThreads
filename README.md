# Mandelbrot Fractal Generator

This program generates a Mandelbrot fractal image using multi-threading. It computes the iterations for each pixel in the image and saves the result as a bitmap image.

## Author

- Name: Aman Hogan-Bailey
- ID: 1001830469

## Dependencies

- bitmap.h
- getop.h
- stdlib.h
- stdio.h
- math.h
- errno.h
- string.h
- sys/time.h
- pthread.h

## Usage

```shell
mandel [options]
```

### Options

- `-m <max>`: The maximum number of iterations per point. (default=1000)
- `-n <threads>`: The total number of threads used to find the Mandelbrot.
- `-x <coord>`: X coordinate of the image center point. (default=0)
- `-y <coord>`: Y coordinate of the image center point. (default=0)
- `-s <scale>`: Scale of the image in Mandelbrot coordinates. (default=4)
- `-W <pixels>`: Width of the image in pixels. (default=500)
- `-H <pixels>`: Height of the image in pixels. (default=500)
- `-o <file>`: Set output file. (default=mandel.bmp)
- `-h`: Show help text.

### Examples

```shell
mandel -x -0.5 -y -0.5 -s 0.2
mandel -x -0.38 -y -0.665 -s 0.05 -m 100
mandel -x 0.286932 -y 0.014287 -s 0.0005 -m 1000
```

## Description

The program uses multi-threading to compute the Mandelbrot fractal image. It divides the image into multiple regions, and each thread is responsible for computing the pixels in its assigned region. The parameters for each thread, such as the image dimensions, center coordinates, scale, and maximum iterations, can be adjusted using command-line options.

The `compute_image` function is called by each thread to calculate the iterations for the pixels in its region. It uses the `iterations_at_point` function to determine the number of iterations at a specific point in the Mandelbrot space. The `iteration_to_color` function converts the iteration count to an RGBA color value.

The resulting image is saved as a bitmap using the `bitmap_save` function. The output file name can be specified using the `-o` option.

## Performance

The program measures the execution time using the `gettimeofday` function. The start time is recorded before the computation begins, and the end time is recorded after the image is saved. The elapsed time is then calculated and displayed in seconds.

## License

This program is provided under the [MIT License](LICENSE).
