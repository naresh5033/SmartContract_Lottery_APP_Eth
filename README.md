## The Hardhat Lottery

In this we'll create a lottery project with Hardhat, where the participants has to pay some fee to enter in to the raffle.\
It will take certain time for the raffle to end, once the dead line is finished the contract will pick a random winner(by automatically) amongst the particpants and trasfer(by call fn) all the balance of the contract to the winner.\
Once it pick up the winner, the players[] and the current Timestamp will be resets to initial state.\
This smart contract (that we deployed) alomost had no maintanance and nobody ever ve to touch(triggers) it again. \
And it will automatically run forever..

### Chainlink VRF

We will use chainlink's VRF fn to pick a random winner (since the deterministic s/m like BC its impossible to have a true random number) from our contract.\
To get the VRF from the chainlink we need to create a subscription (in chain link) which is basically a tx, now we ve an acc where we can fund(links), and we can use that acc for all of our randomness reqs.\
once we added the funds we can add the consumer contracts(VRFv2Consumer.sol --> we can specify the no of randnumbs we want) deploy that contract and add that as consumer addr in VRF, now by doing this we authorize our consumer contract to make a req for randomness.\
In the subscription manager we can see the event history that shows how much links we spent for getting the random number\
The rand numb is uint256 a BN to mach with our players array(which is very small) we can use modulo op --> players[] % randnumb --> the reminder is the answer we use to pick the winner(uint256 indexOfWinner)

### Chainlink Keeper

To automate our contracts and give them access to off-chain computation\
we will also use Chainlink's keeper to trigger the event automatically, once the keepers kick it off, they will pick a random(by VRF) winner from the players[].\
This keepers(AutomationCounter.sol) uses 2 fns checkUpkeep(does offchain computation) and performUpKeep(), we to deploy this keeper contract.\
Then we ve to register for the new upkeep with the above deployed contract addr, once we registered upkeeps are ready and funded with some links.\
Feom the deployed contract we'll be able to hit the counter() with every specified timestamp (sec), this is how chainlink n/w performs upkeep on our contract. And our balance link will reduced every time we hit the counter()\

## ToDO

1. Get our Subscription ID chainlink VRF and fund some links
2. Deploy our contract using the subs ID `yarn hh deploy --network goerli`--> The deployed contract addr is 0x9523E4910512cBf5a6015610634cadF005Eef5a7 \
3. Register the contract with chainlink VRF and its SubId. (Means we have to tell the consumers now this is the contract that you're looking for) grab the contract addr and add it as consumer. \
4. Register the contract addr(Target contract) with chainlink Keepers.
5. Run Stagging tests `hh test --network goerli`

## FullStack

we will create a full stack next.js app (front end to enter our lottery app, we will connect the BC to our front end) \
we will also host this app in a Decentralized context.\
we use react-moralis pckg --> the hook to connect our frontend to the BC\
We also use web3UIKIT for our dApp

The deployed app at "https://singular-frangollo-68defd.netlify.app/"
