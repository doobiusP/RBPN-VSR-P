# Full-length video upscaling
## Current Progress
### Method
To perform VSR (Video Super Resolution), we perform MISO-SR on the target frame using concatenated neighboring frames and corresponding dense optical flows. The recurrent module of this network repeats itself using subsequent iterations over each of 6 neighboring frames. The input frame is bicubically upscaled to provide a color-correct baseline for the network to add onto. 

![image](https://github.com/doobiusP/RBPN-VSR-P/assets/36434536/77a80756-d288-4435-b7ce-4d75d3146bf9)
*<p align="center" style="font-size:10px"> Fig 3. RBPN (Recurrent-Back-Projection Network) </p>*
