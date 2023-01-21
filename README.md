# Solana Candy Machine V2 + Candy Shop

This repo allows you to sell NFTs through Candy Machine V2 and host your own secondary marketplace with [Candy Shop](https://github.com/storyofsoft/Solana_NFT_marketplace).

Supports the following marketplace configurations:
* Basic SOL marketplace
* Basic custom SPL token marketplace
* Marketplace with single NFT view
* Multi collection marketplace
* Multi currency marketplace


<img width="1363" alt="Screen Shot 2022-04-16 at 3 23 54 PM" src="https://user-images.githubusercontent.com/89616076/163665962-f8f9fa00-2143-4234-bb35-13955b55220e.png">

**Prod-ready Responsive UI** which can be easily customized in 5mn.

All Candy Machine V2 functionalities are implemented, auto detected and maintained up-to-date:

- public mint (with countdown when date in future)
- civic support (gatekeeper)
- whitelist
- presale true / false
- end date / end number (endSettings)
- spl-token to mint

![Candy Machine Preview Image](https://i.ibb.co/h7L0M3G/repo-bg.png)

### Supported Wallets

![Supported Wallets](https://i.ibb.co/DC6Wt66/wallets.png)

For instructions on how to set up a V2 candy machine, please refer to Metaplex's documentation [here](https://docs.metaplex.com/candy-machine-v2/Introduction)

## One-Click Vercel Deployment

One-click solution to clone this project to your GitHub and deploy the prod package on a Vercel.
Your only task will be to customize your GitHub fork of this project and commit updates.
Vercel will automatically deploy new prod packages for each new commit.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2FFulgurus%2Fcandy-machine-v2-responsive-ui&env=REACT_APP_CANDY_MACHINE_ID,REACT_APP_SOLANA_NETWORK,REACT_APP_SOLANA_RPC_HOST&envDescription=Populate%20REACT_APP_CANDY_MACHINE_ID%20with%20your%20candy%20machine%20public%20key%2C%20REACT_APP_SOLANA_NETWORK%20with%20the%20solana%20network%20(devnet%2Fmainnet-beta)%20and%20REACT_APP_SOLANA_RPC_HOST%20with%20the%20RPC%20URL%20(example%20for%20devnet%20%3A%20https%3A%2F%2Fapi.devnet.solana.com)&envLink=https%3A%2F%2Fdocs.solana.com%2Fcluster%2Frpc-endpoints%23mainnet-beta&demo-title=My%20Demo%20Mint%20Page&demo-description=A%20one-click%20generated%20solana%20minting%20responsive%20website.&demo-url=https%3A%2F%2Fwww.mintgatsbyclub.net%2F&demo-image=https%3A%2F%2Fi.imgur.com%2FWWSvkBO.png)

## Getting Set Up

### Prerequisites

**REQUIRE NODEJS VERSION <= 16 (version 17 not supported)**.

* Download a Code Editor such as Visual Studio Code.

* Ensure you have both `nodejs` and `yarn` installed. `nodejs` recommended version is 16.

* Follow the instructions [here](https://docs.solana.com/cli/install-solana-cli-tools) to install the Solana Command Line Toolkit.

* Follow the instructions [here](https://hackmd.io/@levicook/HJcDneEWF) to install the Metaplex Command Line Utility.
  * Installing the Command Line Package is currently an advanced task that will be simplified eventually.

### Installation

#### 1. Fork the project & clone it. Example:

```
git clone https://github.com/storyofsoft/Solana_NFT_marketplace
```

#### 2. Define your environment variables (.env file)

##### For Candy Shop

Rename the `.env.example` file at the root directory to `.env` and update the following variables in the `.env` file :

```
REACT_APP_CANDY_SHOP_CREATOR_ADDRESS=__PLACEHOLDER__
REACT_APP_CANDY_SHOP_TREASURY_MINT=__PLACEHOLDER__
REACT_APP_CANDY_SHOP_PROGRAM_ID=csa8JpYfKSZajP7JzxnJipUL3qagub1z29hLvp578iN
```
You may get these parameters by creating a shop [here](https://candy.liqnft.com/my-shop).

```
REACT_APP_SOLANA_NETWORK=devnet
```

This identifies the Solana network you want to connect to. Options are `devnet`, `testnet`, and `mainnet-beta`.

```
REACT_APP_SOLANA_RPC_HOST=https://api.devnet.solana.com
```

This identifies the RPC server your web app will access the Solana network through.

##### For Candy Machine V2

```
REACT_APP_CANDY_MACHINE_ID=__PLACEHOLDER__
```
set __PLACEHOLDER__ with the candy machine pubkey you get once you upload & create your candy machine in Metaplex project. You can find back the value from the `.cache/temp.json` file of your Metaplex project. This file is created when you run the `ts-node candy-machine-v2-cli.ts upload ...` command.

If you are using a custom SPL Token to MINT, you have two additional environment parameters to set :

```
REACT_APP_SPL_TOKEN_TO_MINT_NAME=
```

Spl-token name to display next the price.

```
REACT_APP_SPL_TOKEN_TO_MINT_DECIMALS=9
```

Spl-token decimals were defined during its creation with --decimals parameter. If you didn't use that parameter, then by default your SPL Token got 9 decimals.

More info about it there : https://spl.solana.com/token

#### 3. Build the project and test. Go to the root project directory and type the commands :

To install dependencies:

```
yarn install
```

To test the app locally in the development mode (localhost:3000) :

```
yarn start
```

To build the production package (generated in build folder of the project) :

```
yarn build
```

#### 4. Customize the website UI :

##### 4.1 `App.css` : update 5 main CSS variables with your custom colors :

```
:root {
  --main-background-color: #343A50;
  --card-background-color: #804980;
  --countdown-background-color: #433765;
  --main-text-color:#F7F6F4;
  --title-text-color:#3CBA8B;
}
```

Next to that, make sure to update background image by overwriting your own background PNG file in src/img folder.

##### 4.2 `public` folder :

- Update existing demo cool cats images (cool-cats.gif, logo.png) with your owns images in project `public` folder. Make sure to name them identically.
- Add your custom website title in `index.html` : `<title>Mint Page</title>`

##### 4.3 `Home.tsx` :

Scroll down down to line 380 (`return <main> [...]`) and start to update all titles/menu/text/images/text... as wished in the whole React HTML block.

That's it ! Enjoy your beautiful candy machine :)


##  Available Commands Recap :

### `yarn start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `yarn eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Need Help ?

You can contact me directly on Email : storyofsoft1024@gmail.com

## To thank me with a small SOL tip :]

`BJ2pca1AvhMNU99eGshgfXHmaJXp9yNSsmKxrtc4Bdqx`
