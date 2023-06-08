Task manager
==============
<img width="100%"  alt="Ubos - End-to-End Software Development Platform" src="https://ubos.tech/wp-content/uploads/2023/03/cropped-Group-21015-1.png">
<h3 align="center">
  <b><a href="https://docs.ubos.tech/books/getting-started">Get Started</a></b>
  •
  <a href="https://community.ubos.tech/">Community</a>
  •
  <a href="https://www.youtube.com/@ubos_tech">Youtube</a>
  •
  <a href="https://discord.com/invite/dt59QaptH2">Discord</a>
  •
  <a href="https://github.com/UBOS-tech">GitHub</a>
  </h3>

<div align="center">
  
  [![Use template](https://ubos.tech/wp-content/uploads/2023/06/download-logo.png)](https://platform.ubos.tech/?templateId=64538a883023c6001004f3af)
  [![Use template](https://ubos.tech/wp-content/uploads/2023/06/Group-19.png)](https://youtu.be/rkc5tKsmDlo)
  
</div>

This template is an example of an AI-powered task management system. The system uses OpenAI and Pinecone APIs to create, prioritize, and execute tasks. The main idea behind this system is that it creates tasks based on the result of previous tasks and a predefined objective. The script then uses OpenAI's natural language processing (NLP) capabilities to create new tasks based on the objective, and Pinecone to store and retrieve task results for context. This is a pared-down version of the original [Task-Driven Autonomous Agent](https://twitter.com/yoheinakajima/status/1640934493489070080?s=20) (Mar 28, 2023).

## How it works
The script works by running an infinite loop that does the following steps:

1. Pulls the first task from the task list.
2. Sends the task to the execution agent, which uses OpenAI's API to complete the task based on the context.
3. Enriches the result and stores it in Pinecone.
4. Creates new tasks and reprioritizes the task list based on the objective and the result of the previous task.
The execution_agent() function is where the OpenAI API is used. It takes two parameters: the objective and the task. It then sends a prompt to OpenAI's API, which returns the result of the task. The prompt consists of a description of the AI system's task, the objective, and the task itself. The result is then returned as a string.

The task_creation_agent() function is where OpenAI's API is used to create new tasks based on the objective and the result of the previous task. The function takes four parameters: the objective, the result of the previous task, the task description, and the current task list. It then sends a prompt to OpenAI's API, which returns a list of new tasks as strings. The function then returns the new tasks as a list of dictionaries, where each dictionary contains the name of the task.

The prioritization_agent() function is where OpenAI's API is used to reprioritize the task list. The function takes one parameter, the ID of the current task. It sends a prompt to OpenAI's API, which returns the reprioritized task list as a numbered list.

Finally, the script uses Pinecone to store and retrieve task results for context. The script creates a Pinecone index based on the table name specified in YOUR_TABLE_NAME variable. Pinecone is then used to store the results of the task in the index, along with the task name and any additional metadata.

## Demo
Creating a configuration
![image](https://user-images.githubusercontent.com/41735477/235854815-58981ad9-55af-4555-aaae-42bfd924f998.png)
Chat demo

[Demo](https://user-images.githubusercontent.com/41735477/235855134-fca592e8-ae8f-427d-9ca8-6267278a4c90.mov)
