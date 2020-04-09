# Xoom

Xoom is used to bind data to HTML elements.

### Prerequisites

This is a [Node.js](https://nodejs.org/en/download/) module. Before you start using xoom, you need to install [Node.js](https://nodejs.org/en/download/) on your system.

### Installing

If your using a brand new project
```bash
npm init
```

```bash
npm install xoom
```

## Quick Start

After installation is complete, you need to import xoom in your file.
```bash
import { xoom } from "./node_modules/xoom/xoom.js";
```

Below is the sample code to initialize xoom variable with some random data.
Yoy can define as many models as required. Here, we have used modelPerson and
modelCars. modelPerson is an JSON Object and modelCars is an nested JSON array.

```bash
var x = new xoom({
        data: {
            modelPerson: { firstName: "John", lastName: "Doe"},
            modelCars: [
                    { name: "Ford", "models": ["Fiesta", "Focus", "Mustang"] },
                    { name: "BMW", "models": ["320", "X3", "X5"] },
                    { name: "Fiat", "models": ["500", "Panda"] }
                ]
        }
    });
```

## Running the tests

        <input type="text" x-model="modelPerson" value="{firstName}">
    
        <input type="text" x-model="modelPerson" value="{lastName}">
      
        <p x-model="modelCars">Car: {0/name}</p>

        <p x-model="modelCars">Car Models: {0/models/0} , {0/models/1} , {0/models/2}</p>

        <p x-model="modelCars">Car Models: {1/models/0} , {1/models/1} , {1/models/2}</p>

        <p x-model="modelCars">Car Models: {2/models/0} , {2/models/1} </p>

## Complete Example

<!DOCTYPE html>
<html>
<head></head>  
<script type="module">

    import { xoom } from "./node_modules/xoom/xoom.js";
    var x = new xoom({
        data: {
            modelPerson: { firstName: "John", lastName: "Doe"},
            modelCars: [
                    { name: "Ford", "models": ["Fiesta", "Focus", "Mustang"] },
                    { name: "BMW", "models": ["320", "X3", "X5"] },
                    { name: "Fiat", "models": ["500", "Panda"] }
                ],
            modelOrders: [
                { orderno: 10001, name: 'Laptop', quantity: 1000 },
                { orderno: 10002, name: 'Mobile', quantity: 2000 },
                { orderno: 10003, name: 'Headphone', quantity: 3000 }
            ]
        }
    });

</script>

<body>

    <form>
        <label for="fname">First Name</label>
        <input type="text" id="fname" name="firstname" placeholder="Your name.." x-model="modelPerson" value="{firstName}">
    
        <label for="lname">Last Name</label>
        <input type="text" id="lname" name="lastname" placeholder="Your last name.." x-model="modelPerson" value="{lastName}">
      
        <label for="lname">Multipath Binding</label>
        <p x-model="modelCars">Car: {0/name}</p>
        <p x-model="modelCars">Car Models: {0/models/0} , {0/models/1} , {0/models/2}</p>
        <p x-model="modelCars">Car Models: {1/models/0} , {1/models/1} , {1/models/2}</p>
        <p x-model="modelCars">Car Models: {2/models/0} , {2/models/1} </p>
    
    </form>

    <table>
      <tr>
          <th>Order</th>
          <th>Name</th>
          <th>Quanity</th>
      </tr>
      <tr x-loop="item of model5">
            <td>{item/orderno}</td>
            <td>{item/name}</td>
            <td>{item/quantity}</td>
        </tr>
  </table>

</body>

</html>

## Authors

* **Ashutosh Rambhal** 