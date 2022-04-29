# Data Driven Based Sound Filtering

In this work, we use a deep learning-based data driven method to design a system to filter some of the frequency components of the sound propagating in an open space. 
One clear example of such problems is the patient room in the hospital, in which, minimum acoustic intensity is desired at the room, while speakers at the hospital call doctors or announce any notes.

In order to frame this problem, we model an open space in COMSOL using acoustics module and record the propagating sounds at the location of two microphones. These acoustic waves have been generated by employing ten speakers at random locations within the open space. Using MATLAB coupled with COMSOL, I generated 20,000 data sets to be used as both training and test sets (see picture B1).  The input values are the location of each speaker (both X and Y) and it’s volume and the time response of those two microphones at the steady state are gathered as the output dataset. Next, the input/output datasets are reversed to design our acoustical system. In order to make sure all the features within the new input datasets are captured, an autoencoder model is employed. As illustrated in picture B2, this autoencoder network is composed of identical blocks (each equipped with residual layer) to first encode the time domain data, and then decode it back to the same input. After training the autoencoder network, the 26th layer in this network is connected to a ResNet model to map the input to the output, respectively.  This is depicted in detail, in the attached picture B3. for both networks, a learning rate scheduler is utilized to reduce the learning rate as the number of iteration increases. The outcome of this network and the comparison between the results obtained using COMSOL and predicted using the proposed network are shown in picture B5 and B6.            
