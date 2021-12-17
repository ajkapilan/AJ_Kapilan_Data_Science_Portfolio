# Neuralimaging Data

Python has a special package called MNE. 
This package allows us to visualize 3d Neuralimaging slices. 
I assume that the code behind MRI machines and the 
softwares it uses to highlight different structures to allow 
radiologist to identify problems within the brain, are based on this basic code. 
Here I give you two examples of MNE code where the first shows 
a visualization of a number of slices of an individuals brain, 
going deep within and out of the structure. 
The second examples shows the highlighting of structures on an 
fMRI image of the horizontal plane of the brain. 

### Example 1
```
fig, axs = plt.subplots(4, 4, figsize=[8, 8])
start = int((vol.shape[0] - 160) / 2 )
stop = int(vol.shape[0] - start)

for x, y in enumerate(range(start, stop, 10)):
    axs.flat[x].imshow(vol[y], cmap='gray')
    axs.flat[x].axis('off')

plt.axis('off')
plt.tight_layout()
plt.show()
```
![image](https://user-images.githubusercontent.com/94637743/146212803-470a54a0-68e1-4c2b-b343-8e23e4948ac3.png)


### Example 2
```
fig, axs = plt.subplots(3, 3, figsize=[10, 10])

start = 20
stop  = 61
step = 5


thresh = np.where((fmri_zstat_data > z_thresh), fmri_zstat_data, np.nan)

for x, z_slice in enumerate(range(start, stop, step)):
    axs.flat[x].imshow(underlay[:,:, z_slice], cmap='gray')
    axs.flat[x].imshow(thresh[:,:,z_slice], cmap='gray')
    axs.flat[x].axis('off')

plt.tight_layout()
plt.show()
```
![image](https://user-images.githubusercontent.com/94637743/146212679-09e67cca-4e3d-4f00-a9c5-cfc50c9891fa.png)
