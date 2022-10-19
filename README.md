This repository was created to host my favourite competed projects to showcase my abilities for potential future employers/collaborators. Below I will give a brief summary and main insights of the projects. For further details please see the jupyter notebooks above.

# Sea Turtle Face Detection with Distributed Machine Learning

<img width="1112" alt="image" src="https://user-images.githubusercontent.com/61107719/196725351-81bb9622-20e8-47f1-b06e-0a45ad94ea69.png">

The main goal of this project was to experiment with different options when trying to distribute ML training between workers on a cluster. 

<img width="375" alt="image" src="https://user-images.githubusercontent.com/61107719/196738255-7133ce05-12a8-41ee-a57b-fbe90f7ddc4a.png">
dask.org  
Dask is a python based API that facilitates distributed computing. It can link to a cluster of multiple workers and one scheduler computers. It provides multiple worflows to achieve distributed storing and manipulation of data. It is the main tool used in this project.

One options explored was using dask delayed to distribute a tensorflow CNN. The other option explored was using a scikit learn MLP classifier which is completly dask supported.

## Computational Time Line Comparison
Dask Delayed Distribution of a Tensorflow CNN (5 epochs)
![image](https://user-images.githubusercontent.com/61107719/196728264-29fb43c6-d1c2-4a93-83ff-43017f1951c6.png)

Dask Distribution of a scikit learn MLP classifier (1 epoch)
![image](https://user-images.githubusercontent.com/61107719/196729074-a719cab6-2836-4dd9-a614-609bef9f2b83.png)

Each row in the images above represents a worker on the cluster. The red color indicates that information is being transfered from another worker. The other colors represent a task pering performed by the worker. Time is on the x axis. You can see that when dask distributes the MLP classifier it does not train in paralell. Each worker will train on the data it has collected and then transfer the weights to the next worker to continue training. This strategy will allow the system to break through memory limitations. Although this system does not help reduce training time. The custom dask delayed distribution of the tensorflow CNN is a stark contrast. It will train in paralell. This could potentially lead to reduced training times for large datasets. The data is also split between the workers allowing to break memory limitations. For the small dataset of 4000 198x198 images the paralell training of the dask delayed CNN did not cause faster training times than the unparalell supported MLP. One epoch took 10min for the CNN and only 1 second for the MLP. This is partially because the MLP is a simpler algorithm that was fed further processed HOG versions of the images. The CNN is a more complex algorithm with more weights to alter and is fed the full color images. It is also partially due to the MLP being dask supported and thus optimised. Dask themselves admit that whilst dask delayed is flexible it is also slow. 




# Investigation of Binary Black Hole Properties and their Effect on Time Delay

# Optimisation of Interferometry Lines of Sight for Future Nuclear Fusion Experiments with the Bayesian Experimental Design Framework
