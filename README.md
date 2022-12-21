# The Role of Environmental Variations in
Evolutionary Robotics: Instructions for replicating the experiments
# env-variations
Replicating the experiments described in the paper "The Role of Environmental Variations in Evolutionary Robotics"

The experiments have been carried out and can be replicated by using [evorobotpy2](https://github.com/snolfi/evorobotpy2) and by modifying the source code as described below. 

To learn to use evorobotpy see the Chapter 13 of the open-access book [Behavioral and Cognitive Robotics: An Adaptive Perspective](https://bacrobotics.com)

Please replace the original file contained in the /evorobotpy2/lib folder with the files contained in this repository and recompile the evo module by following the instructions included in Section 13.5 of the book.  

To set the distribution of the perturbations affecting the motor states to a given fixed value add the instruction:

self.nn.setnoiserange(value) 

in the file ./bin/policy.py after line 200
 
To set the distribution of action perturbation to a value which increase during evaluation episode up to a certain maxvalue add the instruction:
"nrange = 0.01" 
in the file policy.py after the line 205
and the instructions:
  self.nn.setnoiserange(nrange)
  nrange += maxvalue/1000
in the same file after line 206
 
To set the distribution of action perturbations to a value which increase across generations up to a certain maxvalue add the instruction:
  self.policy.nn.setnoiserange((self.steps/self.maxsteps)*maxvalue) 
In the file ./bin/openai-es.py after line 218.
 
To set the distribution of action perturbations to a value during post-evaluation tests specify a number of post-evaluation episodes greater than 1 and add the following instruction:
	if (ntrials > 1)
		self.nn.setnoiserange(value)
in the file ./bin/policy.py after line 205.



