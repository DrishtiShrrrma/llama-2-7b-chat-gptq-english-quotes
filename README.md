####  Results 
![image](https://github.com/DrishtiShrrrma/llama-2-7b-chat-gptq-english-quotes-lora-alpha-analysis/assets/129742046/7634cf06-d5b7-43ec-87f6-b5d450a885ae)


#### Things to Try:

1. Experiment with different values of LoRA parameters (r, lora_alpha, lora_dropout, etc.) to understand their effect on the model's performance and efficiency.
2. does quantization affect the model's stability during training?
3. After training quantized model, fine-tune it on a variety of tasks (e.g., sentiment analysis, summarization, translation) to see how it performs in comparison to the non-quantized model or other baselines.
4. Benchmark the inference speed of the quantized models
5. Analyze the robustness of quantized models. Are they more susceptible to adversarial attacks or out-of-distribution data?
6. Study the generalization capability of quantized models on unseen data or different domains.

#### Tips:

1. Monitor GPU Memory: Use torch.cuda.memory_allocated() and torch.cuda.memory_cached() to monitor GPU memory usage.
2. Clear GPU Cache: Releasing unused memory can help:

![image](https://github.com/DrishtiShrrrma/llama-2-7b-chat-gptq-english-quotes/assets/129742046/91860b8e-c3f6-406a-a7f3-92ac908ea2fb)

![image](https://github.com/DrishtiShrrrma/llama-2-7b-chat-gptq-english-quotes/assets/129742046/379e25ef-71c7-4066-951e-907d8fa5526b)

![image](https://github.com/DrishtiShrrrma/llama-2-7b-chat-gptq-english-quotes/assets/129742046/7d26c68a-e69d-44ff-970f-b676b47076f5)

#### Note: 
1. GPTQ quantization is primarily for text models as of now.
2. With GPTQ quantization, we can quantize language model to 8, 4, 3 or even 2 bits. This comes without a big drop of performance and with faster inference speed.
3. Note that the AutoGPTQ library provides more advanced usage (triton backend, fused attention, fused MLP) that are not integrated with Optimum.
4. Only 4-bit models are supported with exllama kernels for now.
5. It is recommended to disable the exllama kernel when you are finetuning your model with peft.
6. The model parameters themselves remain quantized to 4-bits for the forward pass, but the training process (calculating gradients, weight updates) utilizes the more numerical-friendly half-precision format to accelerate computations.
7. Combining quantization and mixed-precision training tries to leverage the best of both techniques: reduced model size and faster training.
8. value of lora_aplha: The lora_alpha can be thought of as the intensity of the adaptation. Typically, you might start with powers of 2, such as 16, 32, or 64. Begin with smaller values and adjust based on results.








###### References: 

1. https://huggingface.co/docs/transformers/main_classes/quantization
2. 
