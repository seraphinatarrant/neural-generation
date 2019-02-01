# Guide to Learning about Models by Interacting

## Introduction

The goal of this exercise is to gain a greater understanding of what an NLP model has and has not learnt,
via interacting directly with it. 

Instructions for how to interact are in the [Web_Demo_Guide](https://github.com/seraphinatarrant/neural-generation/blob/master/Web_Demo_Guide.md).

You can use both Auto Mode and Interactive Mode to try to learn about the system, or focus on one if you find it more helpful. I expect Interactive Mode will be more helpful.

## Questions and Feedback
Goal:

Try to discover as much as you can about the model's knowledge of language and the world, by playing with it. 

For example:
* What linguistic qualities is it aware of? Types of agreement, etc?
* Has it learnt any causal relationships? What about things like Animacy, etc? 
* What sorts of things make it break down? Are there interesting patterns?

And any more linguistic or world knowledge that you think a model might or should learn.
Please send me your thoughts afterwards [serif@uw.edu](mailto:serif@uw.edu).

Also pay attention to which parts of the UI were most helpful for determining this information and anything you wish you could tweak but can't. 


Note:
The goal isn't to get feedback about the UI or system choices (like specific button functionality or OOV handling).
That feedback is useful (feel free to send it) but the point is to discover how much you can learn about the NLP model by playing with it.

Feel free to share with anyone with any Linguistics or NLP knowledge!

## Useful Information
* The default system live right now is trained on [ROC Stories](http://cs.rochester.edu/nlp/rocstories/). This 
has a relatively small uncased vocab (40k words, whereas most systems have 100k) of mostly short "common sense stories" about jobs and schools and dating. No pirates, unfortunately, or Greek muses, or Proustian sentences.
* Storylines and Stories are both "forward only", that is, they are conditioned on _previous_ text, but not _future_ text. 
e.g. if you write the first 3 story sentences and then generate 2 story sentences, it will generate based on the storyline + the 3 sentences you wrote. 
But if you write the 1st sentence and the last 2 sentences (leaving #2 and #3 blank) and then generate #2 and #3, they will only be based on sentence #1. 
* There is some OOV (Out-Of-Vocabulary) handling (based on both cosine similarity and WordNet), but it's invisible. That's probably annoying for a researcher. 
If you are super curious if some behavior is due to OOV, I can either check for you or give you a script that will check and print the answer via command line.
* Storylines can be one word, or multiple words. Think of them like "keywords": they are important words to guide the model in a particular direction (by having it try to incorporate that word).
* In `Interactive Mode` you have 2 choices under `Advanced`: System 2 and System 3 (3 is the default). System 2 is the Plan-and-Write system. 
System 3 adds a Lexical Diversity and a Relevance discriminator on top of System 2, which rerank the System 2 outputs to try to encourage these qualities.








