# Chatbot
## Introduction

The	Turing	test	is	a	test	of	a	computer’s	ability	to	display	intelligent	behavior equivalent	to	that	of	a	human.	Alan	Turing	introduced	the	test in	his	1950	paper “Computing	Machinery	and	Intelligence”.	Even	though	the	test	has	existed	for	over	60	years,	no	program	has	been	able	to	pass	it; though	some	have	been	close.	

A	chatbot	is	a	computer	program	that	engages	in	written or	spoken	conversation	with	a	human	user.	For	the	developer,	the	goal	is	to	make	the	chatbot	as	intelligent as	possible	and	to	pass	the	Turing	test.	In	1966	Joseph	Weizenbaum	created	a	chatbot called	ELIZA.	It	mimicked	the	responses	of	a	psychotherapist	and	came	very	close	to	passing	the	Turing	test.

Conversational models are a hot topic in artificial intelligence research. Chatbots now can be found in a variety of settings, including customer service applications and online helpdesks. These bots are often powered by retrieval-based models, which output predefined responses to questions of certain forms. In a highly restricted domain like a company’s IT helpdesk, these models may be sufficient, however, they are not robust enough for more general use-cases. Teaching a machine to carry out a meaningful conversation with a human in multiple domains is a research question that is far from solved. Recently, the deep learning boom has allowed for powerful generative models like Google’s Neural Conversational Model, which marks a large step towards multi-domain generative conversational models. In this project, we will implement this kind of model in PyTorch.

Inspiration and basic help for this has come from [Pytorch's tutorial](https://pytorch.org/tutorials/beginner/chatbot_tutorial.html) on building a chatbot.

## Data
The Cornell Movie-Dialogs Corpus is a rich dataset of movie character dialog:

- 220,579 conversational exchanges between 10,292 pairs of movie characters
- 9,035 characters from 617 movies
- 304,713 total utterances

This dataset is large and diverse, and there is a great variation of language formality, time periods, sentiment, etc. Our hope is that this diversity makes our model robust to many forms of inputs and queries.

## Model

The brains of our chatbot is a sequence-to-sequence (seq2seq) model. The goal of a seq2seq model is to take a variable-length sequence as an input, and return a variable-length sequence as an output using a fixed-sized model.

Sutskever et al. discovered that by using two separate recurrent neural nets together, we can accomplish this task. One RNN acts as an encoder, which encodes a variable length input sequence to a fixed-length context vector. In theory, this context vector (the final hidden layer of the RNN) will contain semantic information about the query sentence that is input to the bot. The second RNN is a decoder, which takes an input word and the context vector, and returns a guess for the next word in the sequence and a hidden state to use in the next iteration.

## Results

Looking at the below image, it is clear that the bot is quite dramatic in its responses which might be characteristic of using movie scripts. However, it is able to answer a diverse range of questions and so is quite successful overall.
![example chat](example_chat.png)

## Next Steps
Going forward, a few areas to improve on would be to:
- explore other sources of data which aren't quite as dramatic in its responses
- consider using long-short-term models (LSTM) which would help the chatbot understand context and so the conversation would feel more natural and continuous
- introduce new usability features such as the ability to search wikipedia, etc. for information which is a very basic use case for chatbots
