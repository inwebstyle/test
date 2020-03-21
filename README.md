# iWine API 

* Version: "1.0"
* Terms of service: https://iwine.iot/terms
* License: https://iwine.iot/license
* Production Server: https://api.iwine.iot/data/1.0/
* Contact: email: "iwine_email@iwine.iot"

- - -
**iWine** is a smart wine decanter developed by iWine Solutions. It connects to Wi-Fi and acts as an HTTP server so it can interact with devices from the same local network. The decanter reports the following information: volume of the liquid, alcohol content, sugar content, temperature, and a guess on the type of wine.  You can remotely heat or cool the wine to a certain temperature level or to shake the carafe to saturate the wine with oxygen. The above functionality is implemented through a set of HTTP calls (RESTful API). iWine API describes all necessary API's to implement a mobile client.
- - -

## API Calls

### GET /status

**Retrieve decanter contents data**: Access the decanter contents data for a selected iWine decanter on your local network.

Parameters:

Label | Type | Value Range | Example | Description
-----|-------|--------|---------|-------------
name | string|  - | `iWineBottle1`| **Decanter Name**. A human-friendly name of the iWine decanter.
id | string|  - | `abc12348`| **Decanter ID**. A machine name of the iWine decanter. 
vol | string|  - | `250`| **Volume**. Volume of the liquid in mililiters (mL). 
temp | int| 0-100 | `45`| **Temperature**. Temperature of the liquid in degrees Celsius.
alc | number|  0-90 | `12.5`| **Alcohol Content**. Alcohol content of the liquid in %.
sug | int| 0-250 | `10`| **Sugar Content**. Sugar content of the liquid in g/L.
type | string| array {red, white, rose, orange} |`red`| **Wine Type**. Type of the wine in the iWine decanter. Possible values: `red`, `white`, `rose`, and `orange`. Must be used together with `type-guess`.
type-guess | number| 0-1 | `0.5`| **Wine Type Guess Confidence Coefficient**. As the type of the wine in the iWine decanter is determined using machine learning algorithms, it is accompanied by a certain confidence coefficient. Must be used together with `type`. *Example: *.
vibr | string| array{on,off}| `on`| **Vibration** on/off. Shows if the decanter is currently shaking. Possible values: `on` and `off`. Default value is `off`.

#### Responses
        
Successful Response

    {
      "name": "iWineBottle1",
      "id": "abc12348",
      "vol": 1000,
      "temp": 45,
      "alc": 12,
      "sug": 10,
      "type": "red",
      "type-guess": 0.5,
      "vibr": "On"
    }


Not-Found Response

        404:
          description: Not found response
          content:
            text/plain:
              schema:
                title: Weather not found
                type: string
                example: Not found
  

### PUT /temp

### PUT /vibr


   
