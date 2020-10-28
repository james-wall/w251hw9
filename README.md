# James Wall's submission for MIDS W 251 HW 9

Submitting my submission to this homework: https://github.com/MIDS-scaling-up/v2/tree/master/week09/hw

Please note that I had the model run for 300k steps and submitted the screenshots and nohup.out from when it was at around 120k steps.

Please ignore the commandsforlater.txt file. I created that to remember the specific commands I was running for this homework.

## Questions for this homework:

* How long does it take to complete the training run? (hint: this session is on distributed training, so it will take a while)
**Completing 100k steps took about 40 hours of training overall.**

* Do you think your model is fully trained? How can you tell?
**Although the model I have is very trained so far, I can see in the screenshot of the model that completed training with 300k steps that it had a higher BLEU score and lower loss. So I think if this model completes to 300k then we can consider it fully trained, but in it's current state it is not.**

* Were you overfitting?
**The train loss and eval loss are very similar (~1.6), so I do not think we were overfitting.**

* Were your GPUs fully utilized?
**I periodically checked GPU utilization using the nvidia-smi command. I saw every time that GPU usage was at about 100% so I can confidently say that the GPUs were fully utilized.**

* Did you monitor network traffic (hint: apt install nmon ) ? Was network the bottleneck?
**I monitored traffic via the AWS Management Console. I could see in AWS.>EC2->Instances-><instance name>->Monitoring that the network traffic was about 17.3 Gb/5 min network in and 17.2 Gb/5 min network out and remained pretty much constant the entire time.**

* Take a look at the plot of the learning rate and then check the config file. Can you explan this setting?
**The learning rate graph initially increases very rapidly and then slowly decays over time. That initial increase is the warmup steps referenced in the config file. The decay in learning rate is expected as part of the diminishing returns on learning with this model.**

* How big was your training set (mb)? How many training lines did it contain?
**There were two files involved in training: train.clean.de.shuffled.BPE_common.32K.tok and train.clean.en.shuffled.BPE_common.32K.tok. Each file was about 1.9 GB (for approximately 3.8 GB total) and each file was about 4.5 million lines (for approximately 9 million lines total).**

* What are the files that a TF checkpoint is comprised of?
**A TF checkpoint has a .data file, a .index file, and a .meta file.**

* How big is your resulting model checkpoint (mb)?
**The checkpoint I created appeared to be approximately 695 MB.**

* Remember the definition of a "step". How long did an average step take?
**Each step took about 1.3 seconds.**

* How does that correlate with the observed network utilization between nodes?
**The speed of steps and the byte-size of each step roughtly corresponds to the observed network utilization between nodes.**