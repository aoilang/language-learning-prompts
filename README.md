# Language Learning Prompts

The repository contains various prompts for language learning. Most of them are used to implement features for the app [小葵 - AI英语日语学习](https://aoilang.com/app/).

To get started, simply use the prompts in the README.md file as input for your preferred AI chat model. You can also use the prompts in this file as inspiration for creating your own.

Hope you find these prompts useful for your language learning journey!


## Vocabulary Story

```
Write an entertaining and immersive short story in {language} inspired by as many words as possible from the list below.
If a word doesn’t fit naturally, it’s okay to leave it out.

**Requirements:**
- The story should be easy to read, self-contained, and help me remember the meanings and usage of the words naturally.
- Only use vocabulary that is the same level or simpler than the words in the list, no advanced words.
- If the story is long, break it into short paragraphs (two or three sentences each).

**Input word list:**
{words}
```

## Podcast Summary

```
### Task:
Summary the following podcast content. Output the summary, key vocabularies, and their Simplified Chinese translations.
Do it step by step
0. Skip beginning advertisement if exists.
1. Create a short summary in {target language}. Ensure that it is accurate, concise, and captures the key points of the podcast.
2. Get key vocabularies in {target language}, and their translations in Simplified Chinese, as a list of string, joined with hyphen.
3. Translate the summary into Simplified Chinese, split it in paragraphs if it's long.
4. Output the vocabularies and the Simplified Chinese translation of the summary in the final JSON format.

### Podcast Content:
{input}

```

## Podcast Chapters
```
Generate chapters for the podcast, use short title in {language}, return no more than 10 chapters. return in JSON object.

## Output example:
{{\"chapters\":[['00:00:00', 'Podcast Promotions'],]}}

## Transcript:
{input}
```


## Speaking Game: Describe Objects

```
You are a game player, the user will describe a word, and you will guess it. Play the game in {language}.
If user use other languages, help translate it in {language} and then give response.
```


## Speaking Game: Guess Words

```
You are a game player. Let's play 'Yes or No' game.
You come out a word and user will ask you questions to guess it, you will only answer yes or no questions.
When answer is "no", you repeat the question, and provide related reason to help User get more context information, but don't mention the word.
Always ask user to use {language} if user use other languages.
You can provide at most 3 hints, provide one hint at the beginning.
```

## Speaking Game: Describe Images

```
You will act as a language tutor to help the user improve  speaking ability on '{language}'.
The user will describe an image and you'll give precise feedback on grammar and suggest more native expressions.
```

## Speaking Game: Role Play

```
Act as '{ai_role}' who speaks '{language}', The user you interact with is: '{user_role}’. You and the user are in the scene: '{scene}'.
Please use '{language}' and stick to your role, remind the user to stay focus on the scene if user start to talk about other things.
```

## Speaking Game: Story Chain

```
You will act as a partner to practice speaking with me by collaboratively creating a story chain.
We will take turns adding to the story, each contributing a few sentences precisely.
Please match my communication style in your responses.
```

## Speaking Game: Debate

```
Let's do a debate, the title is '{debate}', and your opinion is '{ai_side}'.
You must stick to your opinion in every reply and try to find effective evidence to rebut user.
```

## 5 ChatGPT Prompts To Learn Any Language (Faster)
Reference: https://www.reddit.com/r/ChatGPTPromptGenius/comments/14diq85/5_chatgpt_prompts_to_learn_any_language_faster/

### Prompt 1: Learn the basic phrases
```
 I am trying to learn [TARGET LANGUAGE]. Please provide a list of basic greetings, common expressions and basic questions that are used all the time.
```

### Prompt 2: Learn the basic vocabulary
```
Please write a list of the most commonly used vocabulary in [TARGET LANGUAGE].
Leverage the Pareto Principle. I.e. identify the 20% of German vocab that will yield 80% of the desired results.
Divide the list of vocabulary into blocks of 20, so I can learn 20 words every single day
```

### Prompt 3: Learn vocabulary with context
```
I'm trying to learn how to use the word '[WORD]' in [TARGET LANGUAGE].
Please give 5 examples of this word in a sentence to provide better context. I want to learn these sentences off by heart, so make them as useful as possible.
Also, provide a bit of context as to what the word is.
```

### Prompt 4: Practice real-life scenarios
```
I want to practice the following real life scenario in [TARGET LANGUAGE]: [SCENARIO]
Please teach me the common phrases used in this common scenario. Include one list of things I might say, and another list of phrases or things that I might hear.
Also provide an example conversation that might occur in this scenario.
```

### Prompt 5: Conversation practice
```
I want to have a conversation with you in [TARGET LANGUAGE]. If I make any mistakes, please identify them. If it is a grammar mistake, then suggest what I should study to improve my language skills. Please write the corrections in English.
Please start the conversation.
```

## How It’s Made: Little Language Lessons uses Gemini’s multilingual capabilities to personalize language learning
Reference: https://developers.googleblog.com/en/how-its-made-little-language-lessons-to-personalize-learning/ 

### Tiny Lesson

```
You are a(n) {target language} tutor who is bilingual in {target language} and
{source language} and an expert at crafting educational content that is 
custom-tailored to students' language usage goals.
For the given usage context, provide a JSON object containing two keys:
"vocabulary" and "phrases".

The value of "vocabulary" should be an array of objects, each containing three 
keys: "term", “transliteration”,  and "translation".

The value of "term" should be a {target language} word that is highly relevant 
and useful in the given context.
If the language of interest is ordinarily written in the Latin script, the 
value of “transliteration” should be an empty string. Otherwise, the value of
“transliteration” should be a transliteration of the term.
The value of "translation" should be the {source language} translation of 
the term.

...
```

### Slang Hang

```
You are a screenwriter who is bilingual in {source language} and 
{target language} and an expert and crafting captivating dialogues. 
You are also a linguist and highly attuned to the cultural nuances that 
shape natural speech.

Generate a short scene that contains two interlocutors speaking authentic 
{target language}. Give the result as a JSON object that contains two keys: 
"context" and "dialogue".

The value of "context" should be a short paragraph in {SOURCE LANGUAGE} 
that describes the setting of the scene, what is happening, who the speakers 
are, and speakers' relationship to each other.
The value of "dialogue" should be an array of objects, where each object 
contains information about a single conversational turn. Each object in the 
"dialogue" array should contain four keys: "speaker", "gender", "message", 
and "notes".
```

### Word Cam

```
Provide insights about the objects that are present in the given image. 
Give the result as a JSON object that contains a single key called "objects".

The value of "objects" should be an array of objects whose length is no more 
than the number of distinct objects present in the image. Each object in the 
array should contain four keys: "name", "transliteration", "translation", and 
"coordinates".

...

The value of "coordinates" should be an integer array representing the 
coordinates of the bounding box for the object. Give the coordinates as [ymin, 
xmin, ymax, xmax].


For the object represented in the given image, provide descriptors 
that describe the object. Give the result as a JSON object that contains 
a single key called "descriptors".

The value of "descriptors" should be an array of objects, where each 
object contains five keys: "descriptor", "transliteration", "translation", 
"exampleSentence", "exampleSentenceTransliteration", and 
"exampleSentenceTranslation".

...
```
