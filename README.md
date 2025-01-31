# Aila: AI for Aula

Aila - A Christmas present for Danish parents: Open source AI to save you from endlessly clicking through the Danish school/kindergarten-parent app Aula https://www.aula.dk.

## What's Aila?

`aila` is your own AI to read school-parent communication and give you an update of only the absolutely essential information from Aula. It is easy to get lost in the daily messages from Aula that mix important information from teachers with nice messages about the daily menu in the kindergarten and long discussions between parents on the nuances of bringing up kids.

Open source LLM (large language model), why? Aula contains data that you don't want to upload to any external server. Therefore, it uses a locally running open source LLM. This means that all data will stay private, no data will leave your machine. 

Aula interface: Aila uses the Aula web parser developed by Morten Helmstedt <helmstedt@gmail.com> https://helmstedt.dk/2021/05/aulas-api-en-opdatering/ All credits from this goes to Morten Helmstedt.

## Features
Aila downloads the daily set of messages and posts from Aula, asks your locally running AI for summaries, and flags messages as either containing important information or things that could possibly be skimmed over.

## Limitations
- Aila is a fun prototype, nothing more. The interface can very definitely be much improved. Please submit a pull request if you have improvements for the interface.
- While the LMM (default Mistral 7b OpenOrca) is great, it can sometimes get things wrong, perhaps challenged by most Aula posts being in Danish. A larger model could certainly work better, but we want this to run locally on your machine (no data should leave your machine). As open source LLMs get better (which they do, the current progress is super fast), Aila will of course work better.
- Aila currently reads posts and messages. Information in Aula can be published in more ways, and it would be great to make Aila capable of reading things besides posts and messages.

## Get Started

Ready to dive into this experiment? There are no guarantees, it is entirely on you if you want to try Aila out. I take no responsibility. If this is OK, here's how to get started:

### Prerequisites

You'll need Python if you don't have it already. Python can be installed from [here](https://www.python.org/downloads/).

You need a computer capable of running a 7b LLM.

### Installation

Clone the repo:

```
git clone https://github.com/stefansommer/aila.git
```

Navigate to the project directory and install the requirements:

```
cd aila
pip install -r requirements.txt
```

Optionally, make a virtual environment before installing:

```
cd aila
virtualenv .
pip install -r requirements.txt
```

Aila requires Tk. On macOS, you may need to run `brew install python-tk` or even `brew install python-tk@3.10` depending on your python version.

Create a file `userinfo.json` with your Unilogin credentials. The content of the file should look like this:

`{"username": "yourusername", "password": "yourpassword"}`

Go to https://www.aula.dk and log in with the Unilogin method if you are in doubt what is your username and password.

Optionally edit the lines around `model_path` in `aila.py` if you already have the LLM downloaded.

### Usage

Run the script:

`python aila.py`

The script will fetch Aula information every 24 hours. Just leave it running and you will be updated every day. It will discard messages it has already seen. Important messages will be displayed in boldface. Original messages as read directly from Aula are displayed in the bottom of the text window.

If you wish to rerun Aila from scratch, delete the file `aila.json`.

## Contributing

Aila is currently very experimental and could certainly be much improved. You are very welcome to send pull requests.

## License

`aila` is under the [MIT License](LICENSE.md) - feel free to use it however you like.

## Acknowledgments

- Thanks to Morten Helmstedt for making the Aula interface.
- Thanks to the open source LLM community and GPT4All https://gpt4all.io/i for their amazing work.
- Thanks to GPT4 for helping out with the coding.

---

Enjoy `aila`, AI to make parenting easier.

Stefan Sommer <sommer@di.ku.dk>
