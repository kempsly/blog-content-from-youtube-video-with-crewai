---

# Blog Content Creator from YouTube Videos

This project automates the process of researching and writing blog content based on YouTube videos. It leverages agents for YouTube video transcription and tech blog writing, allowing for seamless content generation from video data. The workflow uses the CrewAI framework to manage tasks and agents, making it easy to scale content creation.

## Features

- **YouTube Channel Research**: Extracts relevant video transcriptions from a specified YouTube channel based on a given topic.
- **Tech Blog Writing**: Summarizes video content into a well-crafted blog post that simplifies complex AI, Data Science, Machine Learning, and GenAI topics.
- **Task Automation**: Uses CrewAI agents and tasks for sequential research and writing, streamlining the entire content creation process.
- **Customizable Output**: Generates markdown files (`.md`) containing the blog content.
- **Agent Collaboration**: The agents work together in a crew, where one agent performs research, and the other writes the blog post based on the research findings.

## Project Components

### 1. **Agents**

Two agents are defined in the `agents.py` file:

- **Blog Researcher**:
  - **Role**: Researches video transcriptions from a specified YouTube channel based on a given topic.
  - **Goal**: Extracts relevant transcription for the topic from YouTube videos.
  - **Backstory**: Expert in AI, Data Science, Machine Learning, and GenAI, providing detailed insights from video content.
  - **Tool**: Uses the `YoutubeChannelSearchTool` to search for relevant video data.

- **Blog Writer**:
  - **Role**: Writes blog content based on the transcriptions provided by the researcher.
  - **Goal**: Narrates compelling tech stories from the video content.
  - **Backstory**: Skilled at simplifying complex topics and engaging readers with accessible content.

### 2. **Tasks**

Two tasks are defined in `tasks.py`:

- **Research Task**:
  - **Description**: Gathers detailed video information from the specified YouTube channel.
  - **Output**: A comprehensive 3-paragraph report summarizing the key information from the video related to the given topic.

- **Writing Task**:
  - **Description**: Summarizes the research into a blog post.
  - **Output**: Generates blog content in markdown format (`new-blog-post.md`).

### 3. **Tools**

The `tools.py` file defines the `YoutubeChannelSearchTool`:

- **yt_tool**: A tool that targets the YouTube channel `@krishnaik06` to search and retrieve video data for content creation.

### 4. **Crew and Task Process**

The `crew.py` file organizes the agents and tasks into a structured workflow:

- **Crew Configuration**: Combines the `blog_researcher` and `blog_writer` agents in a sequential task process.
- **Task Execution**: The process is kicked off with a topic input (e.g., "AI VS ML VS DL vs Data Science"), and the crew executes the tasks in sequence. The researcher agent retrieves video data, and the writer agent creates a blog post from it.

## Setup and Installation

### Prerequisites

- Python 3.8+
- [CrewAI](https://crewai.com) framework
- YouTube API Key (if needed for large-scale video searches)

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/kempsly/blog-content-from-youtube-video-with-crewai.git
   cd blog-content-from-youtube-video-with-crewai
   ```

2. **Set up a Python environment** (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**:
   Create a `.env` file in the project root and add the following keys:
   ```bash
   OPENAI_API_KEY=your_openai_api_key
   ```

### Running the Application

1. **Start the CrewAI process**:
   The process starts by initializing the crew and kicking off the task execution.
   ```bash
   python crew.py
   ```

2. **Example Input**:
   The task will start with the input topic, such as:
   ```bash
   inputs={'topic':'AI VS ML VS DL vs Data Science'}
   ```

3. **Output**:
   The final blog content will be written to a file named `new-blog-post.md`.

### Customization

- **YouTube Channel**: You can modify the `youtube_channel_handle` in the `tools.py` file to target a different YouTube channel.
- **Blog Output**: The output format and file name can be customized in the `write_task` configuration in `tasks.py`.

## Project Structure

```bash
.
├── agents.py                  # Agent configurations (researcher and writer)
├── crew.py                    # Main file for starting the crew process
├── tasks.py                   # Task definitions for research and blog writing
├── tools.py                   # YouTube tool configuration
├── new-blog-post.md           # Output blog file (generated after running the tasks)
├── requirements.txt           # Python dependencies
└── README.md                  # Project README file
```

---
