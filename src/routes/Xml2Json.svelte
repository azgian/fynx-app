<script>
	class XMLtoJSON {
		async fromFile(xmlUrl, rstr) {
			const response = await fetch(xmlUrl);
			const xmlText = await response.text();
			const parser = new DOMParser();
			const xmlDoc = parser.parseFromString(xmlText, 'text/xml');
			const jsonStr = this.jsontoStr(this.setJsonObj(xmlDoc));
			return typeof rstr === 'undefined' ? JSON.parse(jsonStr) : jsonStr;
		}

		async fromStr(xmlStr, rstr) {
			const parser = new DOMParser();
			const xmlDoc = parser.parseFromString(xmlStr, 'text/xml');
			const jsonStr = this.jsontoStr(this.setJsonObj(xmlDoc));
			return typeof rstr === 'undefined' ? JSON.parse(jsonStr) : jsonStr;
		}

		setJsonObj(xml) {
			const jsObj = {};
			if (xml.nodeType === 1) {
				if (xml.attributes.length > 0) {
					jsObj['@attributes'] = {};
					for (let j = 0; j < xml.attributes.length; j++) {
						const attribute = xml.attributes.item(j);
						jsObj['@attributes'][attribute.nodeName] = attribute.value;
					}
				}
			} else if (xml.nodeType === 3) {
				jsObj['_value'] = xml.nodeValue.trim();
			}
			if (xml.hasChildNodes()) {
				for (let i = 0; i < xml.childNodes.length; i++) {
					const item = xml.childNodes.item(i);
					const nodeName = item.nodeName;
					if (typeof jsObj[nodeName] === 'undefined') {
						jsObj[nodeName] = this.setJsonObj(item);
					} else {
						if (typeof jsObj[nodeName].push === 'undefined') {
							const old = jsObj[nodeName];
							jsObj[nodeName] = [];
							jsObj[nodeName].push(old);
						}
						jsObj[nodeName].push(this.setJsonObj(item));
					}
				}
			}
			return jsObj;
		}

		jsontoStr(jsObj) {
			let rejsn = JSON.stringify(jsObj, null, 2)
				.replace(/(\\t|\\r|\\n)/g, '')
				.replace(/"",[\n\t\r\s]+""[,]*/g, '')
				.replace(/(\n[\t\s\r]*\n)/g, '')
				.replace(/[\s\t]{2,}""[,]{0,1}/g, '')
				.replace(/"[\s\t]{1,}"[,]{0,1}/g, '')
				.replace(/\[[\t\s]*\]/g, '""');
			return rejsn.indexOf('"parsererror": {') === -1 ? rejsn : 'Invalid XML format';
		}
	}

	const xml2json = new XMLtoJSON();

	// fetch('https://www.example.com/data.xml')
	// 	.then((response) => response.text())
	// 	.then((xml) => {
	// 		const json = xml2json.fromStr(xml);
	// 		console.log(json);
	// 	})
	// 	.catch((error) => console.error(error));

	const xml = `
	<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE paymentService PUBLIC "-//WorldPay//DTD WorldPay PaymentService v1//EN" 
  "http://dtd.worldpay.com/paymentService_v1.dtd">
<paymentService version="1.4" merchantCode="YOUR_MERCHANT_CODE">
  <reply>
    <orderStatus orderCode="YOUR_ORDER_CODE">
       <payment>
        <paymentMethod>
          KOOKMIN_CREDIT-SSL
        </paymentMethod>
        <amount value="300" currencyCode="KRW" exponent="0" debitCreditIndicator="credit"/>
        <lastEvent>
          CAPTURED
        </lastEvent>
        <balance accountType="IN_PROCESS_AUTHORISED">
          <amount value="300" currencyCode="KRW" exponent="0" debitCreditIndicator="credit"/>
        </balance>
        <cardNumber>
          4523********2507
        </cardNumber>
      </payment>
    </orderStatus>
  </reply>
</paymentService>
	`;
	const json = xml2json.fromStr(xml);
	console.log(json);
</script>
