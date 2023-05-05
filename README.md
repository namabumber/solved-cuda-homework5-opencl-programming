Download Link: https://assignmentchef.com/product/solved-cuda-homework5-opencl-programming
<br>
The purpose of this assignment is to familiarize yourself with OpenCL programming.

A histogram is a statistic that shows frequency of a certain occurrence within a data set. The histogram of an image provides a frequency distribution of pixel values in the image. If the image is a color image, the pixel value can be the luminosity value of each pixel or the individual red (R), green (G), and blue (B). More about image histogram can be found at <a href="https://en.wikipedia.org/wiki/Image_histogram">http://en.wikipedia.org/wiki/Image</a> <a href="https://en.wikipedia.org/wiki/Image_histogram">histogram</a>.

In this problem, you need to use OpenCL to parallelize the implementation of the image histogram. The input/output is a bitmap image format, which stores R/G/B values of each pixel. See the reference code for how to read/write a bitmap file.

Below shows a serial implementation of the image histogram. The complete implementation can be downloaded at <a href="http://people.cs.nctu.edu.tw/~ypyou/courses/PP-f19/assignments/HW5/image-histogram.cpp">http://people.cs.nctu.edu.tw/</a><a href="http://people.cs.nctu.edu.tw/~ypyou/courses/PP-f19/assignments/HW5/image-histogram.cpp"><sub>∼</sub></a><a href="http://people.cs.nctu.edu.tw/~ypyou/courses/PP-f19/assignments/HW5/image-histogram.cpp">ypyou/courses/PP-f19/assignments/HW5/image-histogram. </a><a href="http://people.cs.nctu.edu.tw/~ypyou/courses/PP-f19/assignments/HW5/image-histogram.cpp">cpp</a>.

<table width="610">

 <tbody>

  <tr>

   <td width="610">void histogram(Image *img,uint32_t R[256],uint32_t G[256],uint32_t B[256]){ std::fill(R, R+256, 0); std::fill(G, G+256, 0); std::fill(B, B+256, 0);for (int i = 0; i &lt; img-&gt;size; i++){ RGB &amp;pixel = img-&gt;data[i];R[pixel.R]++;G[pixel.G]++;B[pixel.B]++;}}</td>

  </tr>

 </tbody>

</table>

<h1>2           Input/Output</h1>

<h2>2.1          Input</h2>

The program takes at least one command argument, which indicates the input file name.

./histogram test1.bmp test2.bmp test3.bmp

Figure 1: A sample image

<h2>2.2          Output</h2>

You will need to output a processed file, named hist &lt;input filename&gt;.bmp, for each input file. You can use the reference code to output histogram file(s) directly.

Figure 2: the histogram of sample image

<h1>3           Requirements</h1>

<ul>

 <li>Your submitted solution contains two source files, which are named cpp and histogram.cl.</li>

 <li>The cl must be the OpenCL kernel that you wrote.</li>

</ul>

<h1>4           Development Environment</h1>

<h2>4.1          Building the OpenCL environment on your own computer</h2>

If you have a nVidia or AMD GPU, you can build your own development environment by installing the corresponding SDK.

<a href="https://developer.nvidia.com/cuda-downloads">https://developer.nvidia.com/cuda-downloads </a><a href="http://developer.amd.com/tools-and-sdks/heterogeneous-computing/amd-accelerated-parallel-processing-app-sdk/downloads/">http://developer.amd.com/tools-and-sdks/heterogeneous-computing/amd-accelerated-parallel-processing-app-sdk/ </a><a href="http://developer.amd.com/tools-and-sdks/heterogeneous-computing/amd-accelerated-parallel-processing-app-sdk/downloads/">downloads/</a>

<h2>4.2          Using CUDA/OpenCL Server</h2>

We have set up four servers (the same servers as described in the last assignment) for this assignment. You can login to one of the servers to work on your assignment. Each server contains a GPU. TAs will grade your implementation on these servers, so please make sure your implementation works on the provided servers.

<strong>4.2.1          SSH Login Information</strong>

<table width="400">

 <tbody>

  <tr>

   <td width="107">IP</td>

   <td width="89">Port</td>

   <td width="88">User Name</td>

   <td width="117">Password</td>

  </tr>

  <tr>

   <td width="107">140.113.215.195</td>

   <td width="89">37031–37034</td>

   <td width="88">[Student ID]</td>

   <td width="117">[Provided by TA]</td>

  </tr>

 </tbody>

</table>

<strong>4.2.2 Compilation </strong>g++ histogram.cpp -o histogram -lOpenCL

If the message below shows, do not bother with it.The OpenCL environment works as expected. ”/opt/cuda/lib64/libOpenCL.so.1: no version information available”