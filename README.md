# Introduction 
This package has getCardHash method for JUNO API (juno.com.br).

# Sample: getCardHash

## 1. Require Juno.
```javascript
const Juno = require('juno-payment-node');
```

## 2. Declare get card hash function 

```javascript
    private async getCardHash(ccNumber: string, name: string, ccCode: string,
        ccExpiresOnMonth: string, ccExpiresOnYear: string): Promise<string> {
        return new Promise(async (resolve, reject) => {

            let tokenJuno = getJunoPublicKey(); // TODO: Code get key.

            let cardData = {
                cardNumber: ccNumber,
                holderName: name,
                securityCode: ccCode,
                expirationMonth: ccExpiresOnMonth,
                expirationYear: ccExpiresOnYear
            };

            let checkout = new Juno.DirectCheckout(tokenJuno,
                isProd()); // TODO: Code check whether is production or not.

            checkout.getCardHash(cardData, resolve, reject);
        });
    }
``` 

## 3. Make the call.

```javascript
let ccHash = await this.getCardHash  (ccNumber, name, ccCode, ccExpiresOnMonth, ccExpiresOnYear);
```


