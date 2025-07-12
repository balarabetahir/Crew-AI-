# CrewAI 101: Building Multi-Agent AI Systems


- Leverage **CrewAI** to automate multi-agent workflows for intelligent content generation
- Understand the **key components of CrewAI**—agents, tasks, tools, and processes
- Implement **real-world AI collaboration scenarios**
- Develop foundational skills to **extend and scale CrewAI workflows**

## Setup

### Required Libraries

For this lab, we will be using the following Python libraries:

- [`crewai`](https://pypi.org/project/crewai/) – The core framework
- [`crewai-tools`](https://pypi.org/project/crewai-tools/) – Prebuilt tools
- [`langchain`](https://www.langchain.com/) – Core utilities
- [`langchain-community`](https://pypi.org/project/langchain-community/) – Integrations

### Installing Required Libraries

Run the following commands to install the required packages:

```bash
%pip install langchain==0.3.20 | tail -n 1
%pip install crewai==0.80.0 | tail -n 1
%pip install langchain-community==0.3.19 | tail -n 1
%pip install crewai-tools==0.38.0 | tail -n 1
%pip install databricks-sdk==0.57.0| tail -n 1

What is CrewAI?
CrewAI is a cutting-edge framework for building teams of autonomous AI agents that collaborate on complex tasks.

Why CrewAI?
Assigns roles to agents

Equips them with tools

Directs them with goals

How CrewAI Works
Each agent has:

Role: Specialized function

Goal: Guides decisions

Backstory: Provides context

Tools: Specialized resources

Configuration: Setup options

Setting Up SerperDevTool
What is Serper?
A real-time Google Search API for AI agents.

Setup:

python
import os
os.environ['SERPER_API_KEY'] = "your_api_key"
Initialize the tool:

python
from crewai_tools import SerperDevTool
search_tool = SerperDevTool()
Agents in CrewAI
Defining an Agent
python
from crewai import Agent

research_agent = Agent(
  role='Senior Research Analyst',
  goal='Uncover cutting-edge information...',
  backstory="You are an expert researcher...",
  tools=[SerperDevTool()]
)
Tasks in CrewAI
Creating Tasks
python
from crewai import Task

research_task = Task(
  description="Analyze the major {topic}...",
  agent=research_agent,
  expected_output="A detailed report..."
)
CrewAI Workflow
Assembling the Crew
python
from crewai import Crew, Process

crew = Crew(
    agents=[research_agent, writer_agent],
    tasks=[research_task, writer_task],
    process=Process.sequential
)
Running the Workflow
python
result = crew.kickoff(inputs={"topic": "Latest AI breakthroughs"})
Setting Up Our LLM
python
from crewai import LLM

llm = LLM(
    model="watsonx/meta-llama/llama-3-3-70b-instruct",
    base_url="https://us-south.ml.cloud.ibm.com",
    project_id="skills-network",
    max_tokens=2000
)
