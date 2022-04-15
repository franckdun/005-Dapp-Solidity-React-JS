# 005-Dapp-Solidity-React-JS
Comment créer une Dapp avec Solidity et ReactJS (tuto pour débutants)


	chaine Youtube: Ben BK

	Comment créer une Dapp avec Solidity et ReactJS (tuto pour débutants)

	https://youtu.be/poyVa6yd4X8

____________________________________________________________________________________________________________

	Dans cette vidéo, nous allons créer une DAPP avec Solidity, ReactJS et Hardhat ! (une alternative à truffle).

	- Hardhat est une alternative à Truffle, et je préfère Hardhat !
	- Créer un nouveau dossier sur le bureau
	- Ouvrir ce dossier avec Visual Studio Code
	Commençons par créer notre application ReactJS

	- npx create-react-app react-app 

	- Puis cd react-app

	Puis ensuite nous allons installer des dépendances dont nous aurons besoin dans notre projet 


		- npm install ethers hardhat @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers


	ethers : nous permettra avec le front-end d'intéragir avec le contrat intelligent (alternative à web3.js)

	hardhat @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers : hardhat a besoin de ces dépendances dans l'environnement de développement 

	- npx hardhat 
	- "Create a basic sample project" Puis deux fois touche "entrée"
	Ici nous avons différents dossiers, dont le dossier "contracts" et aussi le fichier hardhat-config.js
	- ouvrir hardhat.config.js 
	Ici vous aurez d'abord un import puis une task (tâche) hardhat. Il est aussi possible d'ajouter des tasks. Mais ce qui est important ici c'est le module.exports.
	On va ajouter un network pour pouvoir tester ici notre contrat intelligent ainsi que renseigner la version de Solidity.
	Hardhat chainId 1337 est permet d'avoir comme network la blockchain de test hardhat.

	- module.exports = {
 	 solidity: "0.8.4",
	  paths: {
	    artifacts: './src/artifacts',
	  },
 	 networks: {
	    hardhat: {
 	     chainId: 1337
	    }
	  }
	};


	- Puis ensuite aller dans contracts/Greeter.sol 
	Décrire le contrat intelligent.
	Nous avons besoin lorsque l'on déploie le contrat de renseigner le greeting (dans le constructeur). 
	- Puis aller dans scripts/sample-script.js
	Ici on va voir qu'on a du code qui va nous permettre de déployer le contrat intelligent. 
	- "const Greeter" est une référence vers le contrat que l'on déploie. 
	- "const greeter" ici on déploie le contrat intelligent avec deploy et on passe le texte que l'on veut renseigner au constructeur.
	- await greeter.deployed() on attend jusqu'à que ce contrat intelligent soit déployé.
	- et enfin on fait un console.log pour indiquer l'adresse ethereum sur laquelle le contrat a été déployé. On utilisera cette adresse dans notre front-end. 
	- Renommer ce fichier en "deploy.js" 

	- Puis npx hardhat compile 
	- Ca vient de créer un dossier "artifacts" dans "src"
	Et ici dans artifacts/Contracts : On va voir l'ABI c'est ça qu'on va mettre dans notre front-end pour intéragir avec.

	Déployons ça sur une blockchain de test. Ca sera un noeud local que hardhat nous fourni. 
	- npx hardhat node
	- Lancer une nouvelle console 
	- cd react-app
	- npx hardhat run scripts/deploy.js --network localhost
	- Ca nous indique que le contrat a été déployé à une nouvelle adresse. Pourquoi ? voir deploy.js
	En revenant ici dans l'autre terminal où il y avait les adresses, on voit des informations sur le déploiement.

	- Puis aller dans MetaMask et ajouter l'account 0 dans MetaMask en sélectionnant bien "localhost:8545" en network.

	- Puis lancer "npm start" 
	- Puis changer app.js en suivant le tuto ou en allant sur le lien GitHub ci-dessous.

-------------------------------------------------------------------------
