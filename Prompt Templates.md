# Prompt Templates

Prompt templates help to translate user input and parameters into instructions for a language model. This can be used to guide a model's response, helping it understand the context and generate relevant and coherent language-based output.

Prompt Templates take as input a dictionary, where each key represents a variable in the prompt template to fill in.

Prompt Templates output a PromptValue. This PromptValue can be passed to an LLM or a ChatModel, and can also be cast to a string or a list of messages. The reason this PromptValue exists is to make it easy to switch between strings and messages.

## String PromptTemplates

These prompt templates are used to format a single string, and generally are used for simpler inputs. For example, a common way to construct and use a PromptTemplate is as follows:

```python
from langchain_core.prompts import PromptTemplate

prompt_template = PromptTemplate.from_template("Tell me a joke about {topic}")

prompt_template.invoke({"topic": "cats"})
```

> [!IMPORTANT]
>
> So, why don't we just give a hardcode like Tell me a joke about topic? Here for anything that requires adaptability or is part of a larger system, templates provide much more power and efficiency. It's easy to change such as replace the cats with dogs, birds, etc.



## ChatPromptTemplates

These prompt templates are used to format a list of messages. These "templates" consist of a list of templates themselves. For example, a common way to construct and use a ChatPromptTemplate is as follows:

```python
from langchain_core.prompts import ChatPromptTemplate

prompt_template = ChatPromptTemplate([
    ("system", "You are a helpful assistant"),
    ("user", "Tell me a joke about {topic}")
])

prompt_template.invoke({"topic": "cats"})
```

In the above example, this ChatPromptTemplate will construct two messages when called. The first is a system message, that has no variables to format. The second is a HumanMessage, and will be formatted by the `topic`variable the user passes in.



## MessagesPlaceholder

This prompt template is responsible for adding a list of messages in a particular place. In the above ChatPromptTemplate, we saw how we could format two messages, each one a string. But what if we wanted the user to pass in a list of messages that we would slot into a particular spot? This is how you use MessagesPlaceholder.

```python
from langchain_core.prompts import ChatPromptTemplate, MessagesPlaceholder
from langchain_core.messages import HumanMessage

prompt_template = ChatPromptTemplate([
    ("system", "You are a helpful assistant"),
    MessagesPlaceholder("msgs")
])

prompt_template.invoke({"msgs": [HumanMessage(content="hi!")]})
```

This will produce a list of two messages, the first one being a system message, and the second one being the HumanMessage we passed in. If we had passed in 5 messages, then it would have produced 6 messages in total (the system message plus the 5 passed in). This is useful for letting a list of messages be slotted into a particular spot.

An alternative way to accomplish the same thing without using the `MessagesPlaceholder` class explicitly is:

```python
prompt_template = ChatPromptTemplate([
    ("system", "You are a helpful assistant"),
    ("placeholder", "{msgs}") # <-- This is the changed part
])
```

