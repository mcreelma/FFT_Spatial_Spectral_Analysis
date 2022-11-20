### **Spacial Analysis of Spectral Reflectance**


#### **Initial Visualization**

During my digital signal processing class, we covered a wide variety of techniques for analyzing noise time series data in the 2-dimensional domain. However, at the end of the course, we covered applying many of these techniques to the spatial domain as well. The code from this example can be found at the following link: [https://github.com/mcreelma/Spatial_Spectral_Analysis_Example](https://github.com/mcreelma/Spatial_Spectral_Analysis_Example). For this particular project, I used RGB reflectance data collected by the Landsat 8 platform. This imagery looked at coastal cloud cover in the North American region (Figure 1). I selected a subset of the imagery which presented an easily identifiable spatial repetition pattern in order to facilitate the process. This particular pattern is the result of gravitational waves interacting with the atmospheric water vapor in order to form ridges of condensation long the direction of flow (Rehnberg, 2020) 


![image1](https://user-images.githubusercontent.com/44550282/202879109-c2c77584-a50d-4191-abe7-2aa21c7d7145.png)

Figure 1 - Subsection of Landsat 8 Imagery


#### **1-Dimensional Profile**

 I began by extracting a  1-dimensional profile of the data with a uniform spacial sampling.In order to do this, I chose a subset from the sample imagery and interpolated the values across that subset in order to develop a uniform spatial sampling (Figure 2). Thi gave me the optimal distance of repetition for the reflectance anomalies. By analyzing this daya, I could determine at what spacial extents the visible patterns were repeating. In the case of my imagery, this meant that I could determine what the distance between cloud peaks was, which turned out to be roughly 100 km with a second distribution at roughly 600 km (Figure 2).

![image4](https://user-images.githubusercontent.com/44550282/202879112-1174b756-944f-4742-9220-8f077945c41f.png)

Figure 2 - Subsample and reflectance repetition across the subsample. 	


#### **FFT For Prominent Direction of Flow**

The final step was to us a fast fourier transform on the image in order to determine the predominant direction of flow (Figure 3). The first stem was to use a 2-dimensional fast fourier transform in order to convert the image into the amplitude spectrum, and then apply a shifting algorithm to center the amplitude spectra. This produces a rough image of the predominant direction of frequency shift, but it is still rather noisy. Thus I applied a low-pass gaussian filter (figure 4) in order to smooth this data. This presents us with a much more readable figure that allows us to determine the predominant direction of flow for the subsection of imagery. 

![image2](https://user-images.githubusercontent.com/44550282/202879125-4bddfe47-3ad8-46fe-841a-b097ef821448.png)

Figure 3 - Stages of FFT application used to determine predominant direction of atmospheric flow



![image3](https://user-images.githubusercontent.com/44550282/202879076-514f2a6d-cdef-4849-9fc8-1a037c24b88a.png)



Figure 4 - Low-pass Gaussian Filter applied to the data to smooth and minimize noise


#### **Further Applications**

For my term project for the class, I applied this process to multiple subsections of the same image and overlaid a rough direction of flow for each image (Figures 5, 6). While this process was extremely imprecise, the hope is that it can be automated and applied to varying scales of an image in order to capture predominant atmospheric flow directions at different scales. These directional rasters could then be used to help analyze atmospheric phenomena from a wider variety of data sources than is currently available.

![image5](https://user-images.githubusercontent.com/44550282/202879154-3bc71141-f4c5-4fb7-b940-a771b5e724d8.png)


Figure 5 - Smoothed frequency transforms for all imagery subsets 

![image6](https://user-images.githubusercontent.com/44550282/202879149-9ff4e4db-7c20-417f-802c-c301bd442c52.png)


Figure 6 - Subsets and predominant directions of flow for landsat imagery


#### **Citations**


### 
Klein, R. (2010). Scale-dependent models for atmospheric flows. Annual Review of Fluid Mechanics, 42, 249–274. https://doi.org/10.1146/annurev-fluid-121108-145537


### 
Rehnberg, M. (2020), Successfully simulating atmospheric gravity waves, Eos, 101, https://doi.org/10.1029/2020EO149547. Published on 30 September 2020.


### 
Namias, J., Yuan, X., & Cayan, D. (1987). Persistence of North Pacific Sea Surface Temperature and Atmospheric Flow Patterns. Scripps Institute of Oceanography.


