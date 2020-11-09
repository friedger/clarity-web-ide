# Clarity Web IDE

Clarity Web IDE is based on [Gitpod](https://www.gitpod.io/docs/), an open-source Web IDE for github and gitlab repositories. The design and functionality is inspired by Visual Studio Code. With extra configuration the Web IDE can be adjusted for the type of code hosted in the repo. The configuration for Clarity development can contain:

* Visual Studio Code plugins for Clarity
* [Clarity REPL](https://github.com/lgalabru/clarity-repl)
* [Stacks node](https://github.com/blockstack/stacks-blockchain)
* [Blockstack cli](https://github.com/blockstack/cli-blockstack/tree/feature/stacks-2.0-tx)
* [Sidecar](https://github.com/blockstack/stacks-blockchain-sidecar)
* [Explorer](https://github.com/blockstack/explorer)


## Using Web IDE
1. Open a git repo that is configured to use the Clarity Web IDE in a browser
1. Prefix the url with `https://gitpod.io/#` in the browser like `https://gitpod.io/#https://github.com/friedger/clarity-smart-contracts`
1. Enjoy all the tools

## Videos
* [Introduction videos](https://www.youtube.com/playlist?list=PLA5-mLPrLnHpc6WsieRck1_VE03kuvIAh)

## Setting up your git repo for Clarity Web IDE
1. Add .gitpod.yaml
1. Add .gitpod.Dockerfile
1. Use the gitpod link to enjoy all the tools

### .gitpod.yaml
The gitpod configuration file defines 
* the docker file to be used
* an inital task (it can be as simple as installing dependencies or as complicated as watching files to run tests automatically) 
    - yarn install
* the editor extensions to be installed initially (more extensions can be added from within the IDE)
    - blockstack.clarity@0.0.5:rBhb1NsIYs1/wpFyiyXNdA==
    - lgalabru.clarity-lsp@0.2.66:PEBgheot/B02RfVLfwbzYg==
    - 2gua.rainbow-brackets@0.0.6:Tbu8dTz0i+/bgcKQTQ5b8g==
    
### .gitpod.Dockerfile
The docker image contains the setup for the clarity tools. As the tools are developing fast, currently, it makes sense to clone the repo and build them. In the future, the docker image would use just the released versions.

* Blockstack CLI in `tools` directory
```
RUN mkdir ~/tools
RUN npm install --global @stacks/cli --prefix ~/tools
``` 

* Stacks node in `tools` directory
```
RUN cd ~/tools; git clone https://github.com/blockstack/stacks-blockchain
RUN cd ~/tools/stacks-blockchain/testnet/stacks-node;cargo install --bin stacks-node --path .;
```
