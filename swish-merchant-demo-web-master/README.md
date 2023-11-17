# Swish Merchant Demo Web
## About
This project demonstrates how to integrate the Swish Merchant API in a [Node.js](https://nodejs.org/) backend. It also contains a small web frontend that shows how the demo web can be used.

## Installation
1. Clone this repository
2. Enter the `merchant-demo` directory
3. Run `npm install`

## Running the demo web against Merchant Swish Simulator
By default, the demo web targets the Merchant Swish Simulator which returns mock results. It can also be set to run against production servers using real merchant production certificates. See [Running the demo web with production certificates](#running-the-demo-web-with-production-certificates) for details.

1. Enter the `merchant-demo` directory
2. Run `node app.js`

You should see the following log output in the console:
`Merchant Demo app listening on port 3000`

## Running the demo web with production certificates
The demo web can be set to target production servers to enable creation of real payment requests. In order to do so, you need to perform the following steps:

1. Copy your production key and production certificates to `ssl/prod.key` and `ssl/prod.pem` respectively (see `ssl/Swish_Merchant_TestCertificate_XXX.key` and `ssl/Swish_Merchant_TestCertificate_XXX.pem` for examples on expected content).
2. Add your Swish number as `payeeAlias` to the production configuration in `app.js`: 

	```javascript
	const prodConfig = {
        payeeAlias: "YOUR_PAYEE_ALIAS",
        host: "https://cpc.getswish.net/swish-cpcapi",
        qrHost: "https://mpc.getswish.net/qrg-swish",
        cert: path.resolve(__dirname, 'ssl/prod.pem'),
        key: path.resolve(__dirname, 'ssl/prod.key')
	}
	```

3. Change to using the production config with:

	```javascript
	const config = prodConfig
	```
	
4. Enter the `merchant-demo` directory
5. Run `node app.js`

You should see the following log output in the console:
`Merchant Demo app listening on port 3000`

## Merchant Demo Web Backend
The demo web backend is located in the file `app.js`. The following Merchant API operations are demonstrated in the demo web backend:

* Create payment request
* Get payment request
* Create refund
* Get refund

## Merchant Demo Web Frontend
The demo web frontend can be accessed by opening <127.0.0.1:3000> in a web browser. The following Merchant Flows are demonstrated in the demo web frontend:

* E-commerce payment request
* Q-commerce payment request