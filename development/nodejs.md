# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- Comment développer en utilisant un système de *livereloading* (`nodemon` par exemple) ✔️
- La connexion de mon application à une base de données avec et sans ORM/ODM (avec `mongodb` puis `mongoose` par exemple) ✔️
- Le développement d'une API REST et GraphQL (avec les packages `express` et `graphql` par exemple) ❌ 
- *Bonus : la manipulation des fichiers système avec `fs` et l'utilisation des streams en NodeJS*  ✔️

## 💻 J'utilise

### Un exemple personnel commenté  ✔️

```javascript
// Validation d'un ordre de commande via stripe
exports.createOrder = (session) => {
    const stripe = require('stripe')(process.env.SECRET_KEY)
    stripe.checkout.sessions.listLineItems(
  session.id,
  { limit: 5 },
  async function(err, lineItems) {
    if(lineItems){
        var listLineItems = lineItems
    const presentTime = new Date()
    const deliveryDate = presentTime.setDate(presentTime.getDate() + 5)
    const order = new Order({ 
        stripe_customer_id : session.customer,
        stripe_session_id : session.id, 
        username : session.shipping.name,
        user_address : session.shipping.address,
        product : listLineItems.data,
        order_date : Date.now(),
        order_HT_price : session.amount_subtotal,
        order_price : session.amount_total,
        delivery_date: deliveryDate,
        delivery_price : session.total_details.amount_shipping,
        order_taxes : session.total_details.amount_tax,
        status : `${session.payment_status !== 'paid' ? "awaiting payment" : session.payment_status }`,
    });
    order.save()
    .then(() => {
     console.log("Votre commande a bien été enregistré !"); 
    })
    .catch((error) => {
        console.log(error);
    })
    }
    if(err){
        console.log(err);
        return err
    }
  }
    
);

}

```

### Utilisation dans un projet  ✔️

https://gitlab.com/l2859/back_end
https://gitlab.com/l2859/front_end

Description :

### Utilisation en production si applicable❌

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ 

Description :

## 🌐 J'utilise des ressources
### Doc Node.js
- https://nodejs.org/en/docs/


## 🚧 Je franchis les obstacles

### Point de blocage ❌

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
