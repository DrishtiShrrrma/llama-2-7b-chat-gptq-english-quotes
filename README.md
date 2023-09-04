#### Tips:

1. Monitor GPU Memory: Use torch.cuda.memory_allocated() and torch.cuda.memory_cached() to monitor GPU memory usage.
2. Clear GPU Cache: Releasing unused memory can help:

![image](https://github.com/DrishtiShrrrma/llama-2-7b-chat-gptq-english-quotes/assets/129742046/91860b8e-c3f6-406a-a7f3-92ac908ea2fb)

![image](https://github.com/DrishtiShrrrma/llama-2-7b-chat-gptq-english-quotes/assets/129742046/379e25ef-71c7-4066-951e-907d8fa5526b)

![image](https://github.com/DrishtiShrrrma/llama-2-7b-chat-gptq-english-quotes/assets/129742046/7d26c68a-e69d-44ff-970f-b676b47076f5)

#### Note: 
1. With GPTQ quantization, we can quantize language model to 8, 4, 3 or even 2 bits. This comes without a big drop of performance and with faster inference speed.
2. Note that the AutoGPTQ library provides more advanced usage (triton backend, fused attention, fused MLP) that are not integrated with Optimum.
3. Only 4-bit models are supported with exllama kernels for now. Furthermore, it is recommended to disable the exllama kernel when you are finetuning your model with peft.

###### References: 

1. https://huggingface.co/docs/transformers/main_classes/quantization
2. 
