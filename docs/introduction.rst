Introduction to RML
===================

Radio Interferometry 
--------------------

Interferometers sample the Fourier Transform of the sky brightness distribution.

Graphic showing mock sky brightness, UV, and sampling -> leading to data set.

Model Fitting 
-------------

Traditionally fitting models like Gaussians or disks.

Image Synthesis
---------------

Sometimes we want to just make images. 

Direct Fourier Transform
~~~~~~~~~~~~~~~~~~~~~~~~
One way to do this is inverse FFT, call this the dirty image. This results from setting all unsampled spatial freqs to zero. Leads to a "beam" with a sidelobe response.

Show gridded data and beam representation.

CLEAN 
~~~~~
Image deconvolution.

Show CLEAN gif. Reference CASA routines.


Regularized Maximum Likelihood Imaging 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

As old (er) than CLEAN, referred to as Maximum Entropy. Reference other RML codes for EHT, CASA imaging. 

Idea of Regularizers.

What are we trying to accomplish with MPoL. Solving specific case of spectral line imaging, which poses some specific computational problems. At the same time, trying to make things general.





