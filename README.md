实战一个真实可运行的文档问答工具。
使用：
Python：编写程序
LangChain：处理文档和模型接入
Chroma：保存向量索引
OpenAI Embeddings：将文字转换成向量
embedding模型是从Hugging Face下载到本地的all-MiniLM-L6-v2模型。
LLM使用的是智谱的glm-4-flash模型。

为什么不用DeepSeek API？
A：DeepSeek（深度求索）确实是国内公司，但是它的官方API域名"api.deepseek.com"是海外接入节点，国内家庭宽带经常会出现丢包、握手慢、超时卡死。所以使用智谱的这个模型，可以在做实验的时候免费调用。

在运行的时候一开始一直是这样的输出：
<img width="1155" height="254" alt="image" src="https://github.com/user-attachments/assets/7ad656fc-3dc0-4b44-9ca9-c29bf32092eb" />
无法输出模型的回答。

经排查，发现问题是Anaconda的Python 3.12.4解释器和chromadb的原生扩展（`chromadb_rust_bindings.pyd`）不兼容，跟代码、跟依赖版本都没关系。
因此把原本的.venv备份了一份，然后重新写了一份.venv，换成了官方Python 3.13，之后就可以正常输出了。

<img width="1161" height="797" alt="d66726db230e6d392628e5132fdf571b" src="https://github.com/user-attachments/assets/9647ad64-3c4f-4242-ad90-0d089ca72f3d" />

<img width="1162" height="723" alt="868ffd55852dc612ca9dc59d95c0a542" src="https://github.com/user-attachments/assets/bd8c2f34-41f0-4427-8b42-33881ccac02c" />


