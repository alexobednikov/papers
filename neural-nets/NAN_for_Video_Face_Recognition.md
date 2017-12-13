# Paper

* **Title**: Neural Aggregation Network for Video Face Recognition
* **Authors**: Jiaolong Yang, Peiran Ren, Dongqing Zhang, Dong Chen, Fang Wen, Hongdong Li, Gang Hua
* **Link**: https://arxiv.org/pdf/1603.05474
* **Tags**: Neural Network, Face Recognition
* **Year**: 2016

# Summary

* **What:**
  * They suggest a method to get cumulative single embedding from a sequence of embeddings (i.e get a single face embedding vector from a video)

![Pipeline](images/NAN_for_VideoFaceRecognition/NAN_pipeline.png?raw=true "Pipeline")

* **How:**
  * Use attention mechanism to weight embeddings in a sequence.
  * They suggest two options:
  	1. Single attention block – Universal face feature quality measurement.
       
       ![First attention](images/NAN_for_VideoFaceRecognition/NAN_first_attention_result.png?raw=true "First attention output") ![First attention](images/NAN_for_VideoFaceRecognition/NAN_first_attention_formula.png?raw=true "First attention formula")
       
       Trainable parameter is: *q* (shape = embedding size x 1)
  	2. Cascaded two attention blocks – Content-aware aggregation.
  	
  	   ![Second attention](images/NAN_for_VideoFaceRecognition/NAN_second_attention_results.png?raw=true "Second attention output")
  	   
  	   Trainable parameters are: *W* (shape = embeddings size x embeddings size), *b* (shape = embedding size x 1)
  * Face embedder (could be any CNN) and "Attention blocks" can be trained together in end-to-end manner or separately one-by-one.
  * Training procedure: 
  	* For verification problem they used siamese structure with contrastive loss
  	* For identification problem they used softmax and cross-entropy as loss function
  * No recurrent blocks, but still input size independent 
  
* **Results:**
  * Shows better results than combining via taking average, median, l2/cos closest, etc.
  * Shows state-of-the-art performance on YouTubeFaces dataset
