<div align=center>
<h1>When Large Language Model based Agent Meets User Behavior Analysis: <br> A Novel User Simulation Paradigm</h1>
<a href="https://pypi.org/project/recbole/">
        <img src="https://img.shields.io/pypi/v/recbole" alt="PyPi Latest Release">
    </a>
    <a href="https://anaconda.org/aibox/recbole">
        <img src="https://anaconda.org/aibox/recbole/badges/version.svg" alt="Conda Latest Release">
    </a>
    <img src="https://img.shields.io/badge/License-MIT-blue" alt="license">
    <img src="https://img.shields.io/github/stars/RUC-GSAI/YuLan-RecAgent" alt="license">
</div>

User behavior analysis is crucial in human-centered AI applications. In this field, the collection of sufficient and high-quality user behavior data has always been a fundamental yet challenging problem. An intuitive idea to address this problem is automatically simulating the user behaviors. However, due to the subjective and complex nature of human cognitive processes, reliably simulating the user behavior is difficult. Recently, large language models (LLM) have obtained remarkable successes, showing great potential to achieve human-like intelligence. We argue that these models present significant opportunities for reliable user simulation, and have the potential to revolutionize traditional study paradigms in user behavior analysis. In this paper, we take recommender system as an example to explore the potential of using LLM for user simulation. Specifically, we regard each user as an LLM-based autonomous agent, and let different agents freely communicate, behave and evolve in a virtual simulator called RecAgent. For comprehensively simulation, we not only consider the behaviors within the recommender system (e.g., item browsing and clicking), but also accounts for external influential factors, such as, friend chatting and social advertisement. Our simulator contains at most 1000 agents, and each agent is composed of a profiling module, a memory module and an action module, enabling it to behave consistently, reasonably and reliably. In addition, to more flexibly operate our simulator, we also design two global functions including real-human playing and system intervention. To evaluate the effectiveness of our simulator, we conduct extensive experiments from both agent and system perspectives. You can get the introduction video of RecAgent through the [Baidu Netdisk](https://pan.baidu.com/s/1n2WeWsiKRiz0ZKZuB0LUZA)(Password: 8sjj) or [Google Drive](https://drive.google.com/file/d/1nTRH2Kvo-1K-s8pB5cl0WbQLt0wCLA0D/view?usp=sharing).

<p align="center">
  <img src="asset/img/framework.png" alt="RecAgnet Framework" width="100%">
  <br>
  <b>Figure 1</b>: RecAgent Framework
</p>


## 🔥 News
- [15/2/2024] RecAgent `v3.0` is released on arXiv with following updates: 
  - 📖 Updated paper and diagrams
  - 🧠 Added new experiments to validate RecAgent's believablity in simulating real human
  - 🔬 Utilized RecAgent to simulate the phenomena of **information cocoons** and **user conformity behavior**
  - ⚙️ Integrated MF as a recommendation algorithm, capable of being trained in real-time during simulations
  
- [9/18/2023] RecAgent `v2.0` is released on arXiv with following updates: 

    -  More Agents: from 25 to at most 1000
    -  Human-like Memory Mechanism
    -  Comprehensive Experiment
    -  System-level and Agent-level Intervention
    -  Human Involved Simulation
        
- [6/5/2023] RecAgent `v1.0` is released on arXiv: [When Large Language Model based Agent Meets User Behavior Analysis: A Novel User Simulation Paradigm](https://arxiv.org/abs/2306.02552)


## Table of Contents


- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
  - [1. Example](#1-example)
  - [2. Website Demo](#2-website-demo)
- [Data](#data)
- [Maintainers](#maintainers)
- [License](#license)
- [Citation](#citation)

## 💡 Features

- **Novel User Simulation Paradigm:** RecAgent is a novel user simulation paradigm that combines large language models (LLMs) with user behavior analysis. It is designed to simulate the behavior of real users in a recommender system. It also replicates users' social interactions, including chatting and posting. RecAgent can be used to evaluate the performance of recommender systems and to generate user behavior data for training and testing. 

- **Human-like Memory Mechanism:** RecAgent's memory mechanism mimics human cognitive processes, divided into sensory memory, short-term memory, and long-term memory. Through efficient compression and scoring of observations, it ensures the relevance and timeliness of information. By combining relevant memory with high-level insights, it achieves more realistic and consistent simulation of user behaviors. 

- **Large Scale Multi-Agent Simulation:** RecAgent is designed for robust, large-scale multi-agent parallel simulations. Seamlessly integrated with multiple OpenAI APIs, it support the capacity to simultaneously engage up to **1000** agents in its simulations. 

- **Multi-dimensional Evaluation:** We conducted an evaluation from two perspectives, that of the agent and that of the system. From the perspective of the agent, we assessed the effectiveness of various types of memory and evaluated whether the agent could access information-rich and relevant memories based on different memory structures. From the system's perspective, we focused on the reliability of the user behavior generated by our system and assessed the efficiency of the simulation.

- **High Extensibility:** RecAgent is designed to support a variety of recommendation algorithms and is equally compatible with multiple LLMs. Both aspects come with interfaces that are easy to customize.

- **Real-time Training and Updating:** RecAgent features an advanced mechanism for real-time training and updating of recommendation models. This allows for the continuous improvement of recommendations based on the latest user interactions and behaviors within the simulation, ensuring that the recommendation system remains dynamic and adaptive to new patterns and preferences.

- **Human-in-the-loop Simulation:** Individuals can create their own Agent to role-play and participate in the entire simulation process. Real people can take the same actions as other Agents, such as watching recommended movies, chatting with other Agents, or posting publicly.

- **Flexible Intervention and Control:** RecAgent provides diverse means to intervene with Agents and monitor the results. An Agent's profile can be freely modified. Moreover, people can intervene with Agents through dialogue. RecAgent also supports saving checkpoints, facilitating retrospective analysis and counterfactual studies.


## 🛠 Installation

To install RecAgent, one can follow the following steps:

1. Clone the repository:

   ```shell
   git clone https://github.com/RUC-GSAI/YuLan-Rec.git
    ```

2. Install the required dependencies:

   ```shell
   pip install -r requirements.txt
   ```
   Using `pip` to install `faiss` may report an error. One solution is to use `conda install faiss-cpu -c pytorch`.
3. Set your OpenAI API key in the `config/config.yaml` file.

## 📦 Usage

To start using RecAgent, follow these steps:

Configure the simulation parameters in the `config/config.yaml` file.

```yaml
# name of LLM model, 'custom' for custom model
llm: gpt-3.5
# path for item data
item_path: data/item.csv
# path for user data
user_path: data/user.csv
# path for relationship data
relationship_path: data/relationship_1000.csv
# path for save interaction records
interaction_path: data/interaction.csv
# directory name for faiss index
ckpt_path: data/ckpt
index_name: data/faiss_index
# simulator directory name for saving and restoring
simulator_dir: data/simulator
# simulator restoring name
simulator_restore_file_name:
# random seed
seed: 2023
# recommender system model
rec_model: MF
# train epoch number for recommender system model
epoch_num: 10
# batch size for recommender system model
batch_size: 64
# embedding size for recommender system model
embedding_size: 64
# learning rate for recommender system model
lr: 0.001
# number of epochs
round: 50
# number of agents, which cannot exceed the number of user in user.csv
agent_num: 5
# number of items to be recommended in one page
page_size: 5
# temperature for LLM
temperature: 0
# maximum number of tokens for LLM
max_token: 1500
# execution mode, serial or parallel
execution_mode: parallel
# time interval for action of agents. The form is a number + a single letter, and the letter may be s, m, h, d, M, y
interval: 5h
# number of max retries for LLM API
max_retries: 100
# verbose mode
verbose: True
# threshold for agent num
active_agent_threshold: 100
# method for choose agent to be active, random, sample, or marginal
active_method: random
# propability for agent to be active
active_prob: 1
# implementation of agent memory, recagent or GenerativeAgentMemory
agent_memory: recagent
# list of api keys for LLM API
api_keys:
  - xxx
# number of random recommendation, 1,3,5
rec_random_k: 0
# number of random friends, 1,3,5
social_random_k: 0
```

The first `agent_num` users in `user.csv` will be loaded. Note that the `agent_num` in `config.yaml` cannot exceed the total number of users in `user.csv`.

### 1. Example

Run the simulation script:

```shell
python -u simulator.py --config_file config/config.yaml --output_file messages.json --log_file simulation.log
```

`config_file` is the path of the configuration file. `output_file` is the path of the output file, which is a JSON file containing all messages generated during the simulation. `log_file` set the path of the log file.

We will obtain some output like:
```
INFO:17349:os.getpid()=17349
INFO:17349:
active_agent_threshold: 100
active_method: random
active_prob: 1
agent_memory: recagent
agent_num: 5
api_keys: ['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']
batch_size: 64
ckpt_path: data/ckpt
embedding_size: 64
epoch_num: 10
execution_mode: parallel
index_name: data/faiss_index
interaction_path: data/interaction.csv
interval: 5h
item_path: data/item.csv
llm: gpt-3.5
log_file: simulation.log
log_name: 17349
lr: 0.001
max_retries: 100
max_token: 1500
output_file: output/message/messages.json
page_size: 5
play_role: False
rec_model: MF
rec_random_k: 0
recagent_memory: recagent
relationship_path: data/relationship_1000.csv
round: 50
seed: 2023
simulator_dir: data/simulator
simulator_restore_file_name: None
social_random_k: 0
temperature: 0
user_path: data/user_1000.csv
verbose: True
Load faiss db from local
INFO:17349:Time for creating 5 agents: 0.0327298641204834
INFO:17349:Simulator loaded.
  0%|                  | 0/50 [00:00<?, ?it/s]
INFO:17349:Round 1
  0%|                  | 0/10 [00:00<?, ?it/s]
INFO:1422158:Sarah Miller enters the recommender system.
INFO:1422158:Sarah Miller is recommended ['<Casper>;;The movie <Casper > is about a friendly ghost named Casper who lives in a haunted mansion with his three mischievous uncles.', '<The Goonies>;;<The Goonies> is a 1985 adventure-comedy film directed by Richard Donner and produced by Steven Spielberg.', '<One False Move>;;<One False Move> is a crime thriller movie released in 1991.', '<What About Bob?>;;<What About Bob?> is a comedy film about a man named Bob Wiley (played by Bill Murray) who has multiple phobias and anxiety disorders.', '<Phantasm III: Lord of the Dead>;;<Phantasm III: Lord of the Dead> is a horror movie that follows the story of Mike, who is on a mission to stop the Tall Man, a supernatural entity who is responsible for the death of his family.'].
INFO:1422158:Sarah Miller watches ['Casper']
```


### 2. Website Demo

<p align="center">
  <img src="asset/img/interface.GIF" alt="RecAgnet Interface" width="100%">
  <br>
  <b>Figure 2</b>: RecAgent Interface
</p>

Click the *Start* button to start the simulation. The simulation will run for `epoch` rounds. You can click the *Pause* button to pause and the *Reset* button to reset the simulation. The demo supports both serial and parallel execution modes. The agent's profile, activity status, system data, and log information are all displayed in real-time on the interface.

## 📚 Data

The item data used in the simulation is from [MovieLens-1M](https://www.kaggle.com/datasets/odedgolden/movielens-1m-dataset).
User profiles and relationships between users are fabricated for simulation purposes. We provide the FAISS index of the item data in directory `faiss_index`.

## Awesome LLM-based Agent for Simulation

| Paper                                                | Date  | Description                                                                                                                                                         |
| ---------------------------------------------------- | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Generative Agent](https://arxiv.org/abs/2304.03442) | 04/23 | Constructed a virtual town comprised of 25 autonomous agents                                                                                                        |
| [RecAgent](https://arxiv.org/abs/2306.02552)         | 06/23 | Developed a recommendation system simulation environment, where Agents can interact with the recommendation system or engage with other Agents on a social platform |
| [S^3](https://arxiv.org/abs/2307.14984)              | 07/23 | Created a news event-driven simulation social network, integrating real-world data                                                                                  |
| [Agent4Rec](https://arxiv.org/abs/2307.14984)        | 10/23 | Built a recommendation system simulator based on the MovieLens dataset                                                                                              |
| [Li et al.](https://arxiv.org/abs/2310.10436)        | 10/23 | Introduced a novel LLM-based approach for macroeconomic simulations with human-like decision-making agents,                                                         |
| [WarAgent](https://arxiv.org/abs/2311.17227)         | 11/23 | Utilize LLM-based agent to simulate historical international conflicts                                                                                              |
| [UGI](https://arxiv.org/abs/2312.11813)              | 12/23 | Introduced UGI using LLMs and CityGPT to simulate and address urban complexities through intelligent agent interactions                                             |

## 💪 Maintainers
   
<div>
    <a href="https://github.com/Paitesanshi">@Lei Wang</a>
    <a href="https://github.com/JingsenZhang">@Jingsen Zhang</a>
    <a href="https://github.com/peteryang1031">@Hao Yang</a>
    <a href="https://github.com/zhiyuanc2001">@Zhi-Yuan Chen</a>
    <a href="https://github.com/TangJiakai">@Jiakai Tang</a>
    <a href="https://github.com/nuster1128">@Zeyu Zhang</a>
</div>



## 📖 License

RecAgent uses [MIT License](./LICENSE). All data and code in this project can only be used for academic purposes.

## 📄 Citation
Please cite the following paper as the reference if you use our code. [![Paper](https://img.shields.io/badge/arxiv-PDF-red)](https://arxiv.org/abs/2306.02552.pdf)

```
@misc{wang2024user,
      title={User Behavior Simulation with Large Language Model based Agents}, 
      author={Lei Wang and Jingsen Zhang and Hao Yang and Zhiyuan Chen and Jiakai Tang and Zeyu Zhang and Xu Chen and Yankai Lin and Ruihua Song and Wayne Xin Zhao and Jun Xu and Zhicheng Dou and Jun Wang and Ji-Rong Wen},
      year={2024},
      eprint={2306.02552},
      archivePrefix={arXiv},
      primaryClass={cs.IR}
}
```