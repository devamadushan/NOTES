```
source ~/venvs/ib_bot/bin/activate
```


```python
from ib_insync import *

util.startLoop()

ib = IB()

ib.connect('127.0.0.1', 7497, clientId=15)


contracts = [Forex(pair) for pair in ('EURUSD', 'USDJPY', 'GBPUSD', 'USDCHF', 'USDCAD', 'AUDUSD')]

ib.qualifyContracts(*contracts)

  

eurusd = contracts[0]

while(1):
	for contract in contracts:
		ib.reqMktData(contract, '', False, False)
		ticker = ib.ticker(eurusd)

	ib.sleep(1)
	print(ticker.marketPrice())
```


### **Récupérer la valeur du BTC**
```python
from ib_insync import *

util.startLoop()

  

# Connexion à TWS

ib = IB()

ib.connect('127.0.0.1', 7497, clientId=15)

  

# Définir le contrat pour BTC/USD

contract = Crypto('BTC', 'PAXOS', 'USD') # Bitcoin via PAXOS en USD

ib.qualifyContracts(contract)

  

# Activer les données de marché

ib.reqMktData(contract, '', False, False)

  

print("Données en direct pour BTC/USD (Ctrl+C pour arrêter):")

  

try:

while True:

ticker = ib.ticker(contract)

if ticker.marketPrice() is not None:

print(f"BTC/USD : {ticker.marketPrice():.2f} USD")

else:

print("BTC/USD : Pas de données disponibles")

ib.sleep(1) # Pause de 1 seconde entre les mises à jour

except KeyboardInterrupt:

print("\nArrêt des données en direct.")

finally:

ib.disconnect()
```