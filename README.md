# Full-length video upscaling

## Current Progress

### Method

To perform VSR (Video Super Resolution), we perform MISO-SR on the target frame using concatenated neighboring frames and corresponding dense optical flows. The recurrent module of this network repeats itself using subsequent iterations over each of 6 neighboring frames. The input frame is bicubically upscaled to provide a color-correct baseline for the network to add onto.

![image](https://github.com/doobiusP/RBPN-VSR-P/assets/36434536/77a80756-d288-4435-b7ce-4d75d3146bf9)
_<p align="center" style="font-size:10px"> Fig 3. RBPN (Recurrent-Back-Projection Network) </p>_

### Current setbacks

<ul>
  <li>Training the RBPN was very time-consuming with time for one epoch being around 35 mins. This was due to the limited RAM on free cloud-based GPU services such as Kaggle which could only serve small batch sizes.</li> 
  <li>Had to train with a small dataset which hindered output quality as larger datasets would make training times infeasible. </li>
  <li>Training would often stall and losses tended to oscillate regardless of tuning hyperparameters resulting in blank/totally black outputs after each epoch.</li>
  <li>Problem identified was Gradient Explosion and was mitigated by introducing batch-norm layers; however the oscillating loss was still persistent.</li>
  <li>Could not identify modifications needed to produce color-correct frames with few artifacts. </li>
  <li>Output would capture image structure and content but would fail to perceive the correct colors leading to frames with bright hues.</li>
  <li>Localized patches of intense color would appear over the frames in seemingly random locations producing unwanted artifacts.</li>
  <li>The model is inefficient when used with any video. Example: a 7-second video takes 12 mins to upscale despite using the GPU...</li>
</ul>

### Currently Working On

<ul>
  <li>Designing first draft of website to learn basics of HTML and CSS</li>
  <li>Researching basicVSR++</li>
</ul>

### Further plans

- Develop a seamless and interactive interface to the model via a website using **Flask** as the framework alongside Javascript and HTML/CSS
- Explore basicVSR++ as an alternative to RBPN considering the infeasibility of the model's real-world use case.

### Associated links

- <a href="https://www.kaggle.com/code/doobiusp/rbpn-vsr-v1">Kaggle code</a>

### References

- <a href="https://paperswithcode.com/paper/recurrent-back-projection-network-for-video/review/">Recurrent Back-Projection Network for Video Super-Resolution</a>
- <a href="https://youtu.be/VSSyPskheaE?si=1otPGzA77ieLt2MU">Coarse-to-Fine Flow Estimation | Optical Flow </a>
- <a href="http://toflow.csail.mit.edu/">VIMEO90K dataset</a>
