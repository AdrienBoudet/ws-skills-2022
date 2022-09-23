# Langage Javascript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les `structures` de base du langage  ✔️
- les normes `ecmascript` ✔️
- l'utilisation de l'`asynchrone`  ✔️
- les spécifités du mot-clef `this` ✔️

## 💻 Je code en Javascript

### Un exemple de code commenté  ✔️

```javascript
// méthode Node permettant d'ajouter un produit dans le back d'une boutique d'e-commerce
exports.addNewProduct = (req, res, next) => { 
  var imagesArray = [];
  req.files.forEach(element => {
    imagesArray.push(`${req.protocol}://${req.get('host')}/images/${element.filename}`)
  });

  const product = new Product({
    product_name: req.body.product_name,
    reference: req.body.reference,
    description: req.body.description,
    images: imagesArray,
    price: req.body.price.replace(/\./g, '').replace(',', ''),
    stock: req.body.stock,
    trademark: req.body.trademark,
    required_age: req.body.required_age,
    on_sale_date: Date.now(),
    category: req.body.category,
    subcategory: req.body.subcategory,
    ordered: 0,
    status: req.body.status
  });

  product
    .save()
    .then(() => {
      res.status(201).json({
        message: `Vous avez ajouté ${req.body.product_name} dans la catégorie ${req.body.category}`,
      });
    })
    .catch((error) => {
      if (error.errors.reference) {
        res.status(500).json({
          message:"La référence " + error.errors.reference.value + " est déjà utilisée sur un autre produit"
        })
      }
      else if (error.errors.product_name) {
        res.status(500).json({
          message:"Le nom du produit " + error.errors.product_name.value + " est déjà utilisé"
        })
      }
      else {
        res.status(500).json({
          message: "Une erreur du serveur est survenue, si le problème persite veuillez contacter l'administrateur du site"
        })
      }
    });
};

```

### Utilisation dans un projet ✔️

https://gitlab.com/l2859/back_end
https://gitlab.com/l2859/front_end

Description :

### J'ai utilisé ce langage en production ❌ 

[lien du projet](...)

Description :

### J'ai utilisé ce langage en environement professionnel  ❌

Description :

## 🌐 J'utilise des ressources

### MDN Javascript
https://developer.mozilla.org/fr/docs/Web/JavaScript
### Grafikart
- https://grafikart.fr/tutoriels/javascript
### Openclassroom
- https://openclassrooms.com/fr/courses/6175841-apprenez-a-programmer-avec-javascript
### Stackoverflow
- https://stackoverflow.com/

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️

