# 3D Resume taking about my skills, projects and work experiences. 

Taken Inspiration from Jos Guilherme project. 
Still Making a lot of changes into the project and would post it soon.

 <div align="center">
    <image src='./src/assets/images/thumbnail.png'>
    <a href="https://esgario.github.io/3d-resume/">
        <p>Click here to access the 3D Resume</p>
    </a>
</div>

## Installation

This project is split into two parts:

-   The web app, which is a JavaScript application.
-   The assets generator, which is a Python application.

### JavaScript dependencies

Run the following command to install the dependencies:

```
npm install
```

### Python dependencies

Before installing the dependencies, make sure you have python installed and that you have created a virtual environment.

Run the following command to install the dependencies:

```
pip install -r assets_generator/requirements.txt
```

## Development

### Web APP

Run the following command to start the development server:

```
npx vite src --host 0.0.0.0
```

Building the project with parcel:

```
npx parcel build src/index.html --public-url ./
```

Formatting the code:

```
npx prettier . --write
```

### Assets Generator

Before generating the assets, create a `.env` file in the `assets_generator` folder with the following content:

```
ELEVEN_LABS_API_KEY=<your_api_key>
```

To generate the assets run the following command:

```
python assets_generator/main.py
```

## Generating Avatar

The Avatar used in this project was generated using [Ready Player Me](https://readyplayer.me/) service.

To download the avatar with all the morph targets, use the following URL:

```
https://readyplayer.me/api/avatar/download?avatar=${avatarId}&morphTargets=eyeBlinkLeft,eyeBlinkRight,Oculus Visemes
```

More information about the API can be found [here](https://docs.readyplayer.me/ready-player-me/api-reference/rest-api/avatars/get-3d-avatars).

## Animations

The animations used in this project were downloaded from [Mixamo](https://www.mixamo.com/#/).

## Text to Speech

The audios files are generated using the [Eleven Labs](https://elevenlabs.io/speech-synthesis) service.

Currently this is the only service that I'm paying for, but I'm looking for a free alternative. The voices generated by this service are very good, especially the Portuguese ones.

## Lip Sync

To generate the lip sync animations I'm using the [Rhubarb Lip Sync](https://github.com/DanielSWolf/rhubarb-lip-sync). Given an audio file it generates a JSON file with the morph targets for each phoneme.

The Avatar used in this project uses the Viseme morph targets, so I had to map the phonemes generated by Rhubarb to the Visemes. Here are some useful links:

-   [Viseme reference](http://www.zxthex.com/Viseme%20Reference%20_%20Oculus%20Developers.html)

## Chatbot

To create the chatbot solution I'm using a General Text Embedding model from huggingface. Basically it's a model that receives a text and returns a vector with 384 dimensions. This vector can be used to compare the similarity between two texts.

I've create a .json file with some questions and answers. The questions are used to generate the embeddings and the answers are used to generate the audio files. When the user asks a question, the model will find the most similar question in the .json file and return the corresponding answer. If the similarity is below a certain threshold, the bot will say that it doesn't understand the question.
