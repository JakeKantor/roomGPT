# [RoomGPT](https://roomGPT.io) - redesign your room with AI

This is the previous and open source version of RoomGPT.io (a paid SaaS product). It's the very first version of roomGPT without the auth, payments, or additional features and it's simple to clone, deploy, and play around with.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/Nutlope/roomGPT&env=REPLICATE_API_KEY&project-name=room-GPT&repo-name=roomGPT)

[![Room GPT](./public/screenshot.png)](https://roomGPT.io)

## How it works

It uses an ML model called [ControlNet](https://github.com/lllyasviel/ControlNet) to generate variations of rooms. This application gives you the ability to upload a photo of any room, which will send it through this ML Model using a Next.js API route, and return your generated room. The ML Model is hosted on [Replicate](https://replicate.com) and [Bytescale](https://www.bytescale.com/) is used for image storage.

## Running Locally

### Cloning the repository the local machine.

```bash
git clone https://github.com/Nutlope/roomGPT
```

### Creating a account on Replicate to get an API key.

1. Go to [Replicate](https://replicate.com/) to make an account.
2. Click on your profile picture in the top left corner, and click on "API Tokens".
3. Here you can find your API token. Copy it.

### Storing the API keys in .env

Create a file in root directory of project with env. And store your API key in it, as shown in the .example.env file.

If you'd also like to do rate limiting, create an account on UpStash, create a Redis database, and populate the two environment variables in `.env` as well. If you don't want to do rate limiting, you don't need to make any changes.

### Installing the dependencies.

```bash
npm install
```

### Running the application.

Then, run the application in the command line and it will be available at `http://localhost:3000`.

```bash
npm run dev
```

## One-Click Deploy

Deploy the example using [Vercel](https://vercel.com?utm_source=github&utm_medium=readme&utm_campaign=vercel-examples):

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/Nutlope/roomGPT&env=REPLICATE_API_KEY&project-name=room-GPT&repo-name=roomGPT)

## Quick Start Guide: Building a RoomGPT Project

Welcome to the Quick Start Guide for creating your Room GPT project using the command line. This guide will walk you through setting up your environment, creating a basic GPT-based application focused on room or environment-related tasks.

### Prequisites

Ensure Python 3.6 or later is installed on your system.

### Setup Your Environment

Create Environemnt:

```bash
python -m venv myprojectenv
```

Activate Environment:
Unix/MacOS:

```bash
source myprojectenv/bin/activate
```

Windows:

```bash
myprojectenv\Scripts\activate
```

### Install Required Package

```bash
pip install transformers
```

### Create Project

```bash
mkdir myroomgptproject
cd myroomgptproject
```

### Write Your First Project

This example will demonstrate how to genereate basic room descriptions.

```bash
from transformers import GPT2LMHeadModel, GPT2Tokenizer

def generate_room_description(prompt):
    tokenizer = GPT2Tokenizer.from_pretrained("gpt2")
    model = GPT2LMHeadModel.from_pretrained("gpt2")

    inputs = tokenizer.encode(prompt, return_tensors="pt")
    outputs = model.generate(inputs, max_length=100, num_return_sequences=1)
    text = tokenizer.decode(outputs[0], skip_special_tokens=True)

    return text
```

### Test Your Project

```bash
python example.py
```

## License

This repo is MIT licensed.
