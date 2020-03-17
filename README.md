# Chefbot_NCF

This repository is intended for managing conversations that are interfaced through an application like Google Dialogflow. While such applications are mostly useful for modelling single adjacency pairs in the conversation, Chefbot_NFS is developed to enable the modelling of extended conversation plans, such as instructing a cooking recipe (hence the name chefbot). It is inspired on the Natural Conversation Framework (NFC) proposed by Moore (2019), where the content of the conversation is detached from the act of conversing itself. Furthermore, the Information State Update paradigm (Larsson, 2000) is adopted to keep track of the conversation and enable dynamic conversation management. The patterns of conversational activities and sequences, as proposed by Moore, can be modelled through conversational moves, with their own preconditions and effects.

## Outline

The basic architecture of most conversational systems consists of a dialog management core, a Natural Language Understanding (NLU) part for interpreting the user's utterances and a Natural Language Generation (NLG) part for formulating the intended response to the user utterance. Optionally, this may be appended with modules for decoding and synthesizing speech, gestures and other non-verbal types of communication. Chefbot_NFC is intended for modelling the dialog mangement and NLG. It should be connected to a dialog application that takes care of the NLU part, and possibly the other modules at the periphery of the architecture. 

In its current form, the system is designed for the application of a cooking assistent, in connection with Google Dialogflow. Dialogflow takes care of the NLU, including the recognition of the users intent, as well as Automatic Speech Recognition and Speech Synthesis. This information is communicated through the use of webhooks. 

Chefbot_NFC features the following components (in the 'core' directory):

* infostate_tracker.py
.- for keeping track of and updating the information state
.- for selecting the next conversation moves of the agent
* natural_language_generator.py
.- for selecting the proper agent responses based on the selected conversation moves
* dialog_manager.py 
.- for connecting the agent to Google Dialogflow, parsing incoming messages and posting the agent's response

The utterances of the agent can be written in two files: 

* a file with the standard responses
* a file with the recipes, each recipe consisting of steps and clarifications of steps

Examples of such files are given in the 'example_data' folder. These files are by default used by the dialogue agent. When writing your own content, it is important to use the exact same dictionary keys.

## Usage

The following components are needed to set up the conversational agent:


