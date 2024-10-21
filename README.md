# DeepVigor+; *Fast and Scalable Fault Resilience Analysis Tool for Deep Neural Networks*

DeepVigor+ is an innovative fault resilience analysis tool for CNNs with remarkable scalability, outperforming conventional statistical fault injection while meeting analysis accuracy requirements. With DeepVigor+, emerging CNNs can be analyzed within a few minutes.


# How to run

To exploit the DeepVigor+ tool, there are multiple parameters to be set. It is executed by the following commands:
`python main.py --model=your_cnn  --run-mode=target_run_mode --dataset=dataset --batch-size=batch_size`
The description of each  parameter is as follows:

 - `model`: the name and checkpoint of the pre-trained CNN model should be defined in `load_model` function in  `CNNs.py`, similar to the existing CNNs in the corresponding file.
 - `dataset`
 - `batch-size`
 - `run-mode`: specifies the fault resilience analysis method on weights and activations separately, in both complete and sampling methods, as follows:
	 - ***full-analysis-weight***: complete analysis on all output channels of weights
	 - ***full-analysis-act***: complete analysis on all output activations
	 - ***sampling-analysis-weight***: sampling analysis on output channels of weights, specified by `channel-sampling`
	 - ***sampling-analysis-act***: sampling analysis on output channels of weights, specified by `channel-sampling`
 - `channel-sampling`: is specified in case of `run-mode=sampling-analysis-weight` or `run-mode=sampling-analysis-act`, as a value in *(0, 1)*. *recommended vale: 0.1*

The outputs of the tool are provided based on the specified *run-mode*. In the case of *full-analysis*, the *vulnerability factors* for all neurons/channels are written in separate files for each layer, in a directory: `network_name-dataset_name/run_mode`. Moreover, a log file is created which summarizes the results. 
In the case of sampling analysis, a log file is created in the corresponding directory, reporting the analysis results. 

Obtained results from the tool can be exploited for fault resilience comparison and visualization, as reported in the paper.

It is highly recommended to run the tool on GPU. It is tested with _python 3.10.9_ and _pytorch 2.1.2+cu121_
