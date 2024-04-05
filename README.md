# conky-cryptoMonitor
This conky theme displays real-time prices of Bitcoin, Ethereum, Cardano, Near, Solana, Graph
TraderJoe (JOE) using the [Coingecko-api](https://www.coingecko.com/en/api/documentation).

![](Screenshot.png)

## Dependencies
This script require the follwing modules/libraries: 
* Conky module; which can be installed using: </br>
`sudo apt install conky-all`
* jq: </br>
`sudo apt install jq`

## Installation
1. Dowload the project and extract it to your home folder.
2. Navigate to the folder and run the install script in the terminal using 
```
./install
```

## Change/Add some coins
1. Go to [Coingecko-api docs](https://www.coingecko.com/en/api/documentation) and open the query "GET /simple/price";
2. Press "Try it out" and fill "ids" field with ids of the coins you want (you can find the ids on the specific coin page on [Coingecko](https://www.coingecko.com/en));
3. On "vs_currencies" field put "usd" (and "btc" if you're interested on btc pairs);
4. Modify other fields as you want and press "Execute";
5. Copy the curl string and paste it on the template file (row 56);
6. Then you'll need the image: search it online and make it white please or you'll ruin the minimal feel :(
7. Copy and paste this, then modify img path, positioning, offset, voffset and jq command:
```
${image ~/conky-cryptoMonitor/img/btc-white.png -p 20,75 -s 50x50}${voffset 120}\
${font Ubuntu Regular:size=12}${offset 8}${execi 0 echo "scale=2; $(cat ~/conky-cryptoMonitor/prices.json | jq -r .bitcoin.usd)/1" | bc}\
```
8. Reinstall the widget and enjoy :)

## Tests
This code/script has been tested on Ubuntu 22

