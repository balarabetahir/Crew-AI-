{
  "project": {
    "title": "CrewAI 101: Building Multi-Agent AI Systems",
    "logo": "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/assets/logos/SN_web_lightmode.png",
    "description": "A hands-on lab demonstrating how to build collaborative AI agents using CrewAI to automate content creation workflows.",
    "toc": [
      "Overview",
      "Key Features",
      "Getting Started",
      "Prerequisites",
      "Installation",
      "Workflow Components",
      "Agents",
      "Tasks",
      "Tools",
      "Crew Orchestration",
      "Usage",
      "Example Output",
      "Exercises",
      "Contributing",
      "License",
      "Authors"
    ]
  },
  "overview": {
    "description": "This project demonstrates how to build a multi-agent AI system that transforms raw research into polished blog posts and social media content.",
    "agents": [
      {
        "name": "Research Agent",
        "purpose": "Gathers cutting-edge information using web search tools"
      },
      {
        "name": "Writer Agent",
        "purpose": "Structures findings into engaging blog content"
      },
      {
        "name": "Social Media Agent",
        "purpose": "Creates platform-optimized summaries"
      }
    ]
  },
  "features": [
    "Role-based AI Agents",
    "Real-time Research",
    "Customizable Workflows",
    "LLM Flexibility",
    "Performance Metrics"
  ],
  "getting_started": {
    "prerequisites": [
      "Python 3.8+",
      "SerperDev API key",
      "Basic understanding of Python and AI concepts"
    ],
    "installation": [
      "pip install langchain==0.3.20",
      "pip install crewai==0.80.0",
      "pip install langchain-community==0.3.19",
      "pip install crewai-tools==0.38.0",
      "pip install databricks-sdk==0.57.0"
    ]
  },
  "components": {
    "agents": {
      "description": "Specialized AI team members with defined roles, goals, and capabilities",
      "attributes": [
        "Roles (Researcher, Writer, Strategist)",
        "Specific goals and backstories",
        "Custom tools and capabilities"
      ]
    },
    "tasks": {
      "description": "Discrete work units with clear specifications",
      "attributes": [
        "Clear descriptions",
        "Expected outputs",
        "Designated agents",
        "Optional tools and context"
      ]
    },
    "tools": {
      "description": "Extensions that enhance agent capabilities",
      "examples": [
        "SerperDev for web search",
        "Custom tools for specific domains",
        "LLM integrations"
      ]
    },
    "crew": {
      "description": "The coordination layer that manages workflows",
      "capabilities": [
        "Sequences tasks (sequential or hierarchical)",
        "Manages agent interactions",
        "Handles input/output between components"
      ]
    }
  },
  "usage": {
    "configuration": {
      "description": "Set up API keys",
      "code": "import os\nos.environ['SERPER_API_KEY'] = \"your_api_key_here\""
    },
    "agent_definition": {
      "description": "Create an agent",
      "code": "research_agent = Agent(\n  role='Senior Research Analyst',\n  goal='Uncover cutting-edge information...',\n  backstory=\"You are an expert researcher...\",\n  tools=[SerperDevTool()]\n)"
    },
    "task_definition": {
      "description": "Define a task",
      "code": "research_task = Task(\n  description=\"Analyze the major {topic}...\",\n  agent=research_agent,\n  expected_output=\"A detailed report on {topic}...\"\n)"
    },
    "execution": {
      "description": "Run the crew",
      "code": "crew = Crew(\n    agents=[research_agent, writer_agent],\n    tasks=[research_task, writer_task],\n    process=Process.sequential\n)\n\nresult = crew.kickoff(inputs={\"topic\": \"Latest AI breakthroughs\"})"
    }
  },
  "example_output": {
    "description": "The system produces research reports, blog posts, and social media snippets",
    "structure": {
      "raw": "Final blog post content...",
      "tasks_output": [
        {
          "description": "Research task...",
          "output": "Research findings..."
        },
        {
          "description": "Writing task...",
          "output": "Blog post content..."
        }
      ],
      "token_usage": {
        "total_tokens": 1850,
        "prompt_tokens": 1200,
        "completion_tokens": 650
      }
    }
  },
