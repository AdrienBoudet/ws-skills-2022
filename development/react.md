# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- l'état (_state_) pour contrôler l'affichage d'un composant  ✔️
- les composants enfants et les _props_ qu'on leur passe  ✔️
- le déclenchement d'instructions en fonction des actions de l'utilisateur ✔️
- le déclenchement d'instructions en fonction de l'étape du cycle de vie du composant ou du changement de valeur de ses props ✔️
- l'usage d'un reducer (_useReducer_) pour gérer un état composé dans un composant ❌
- l'état stocké dans un composant avec un _context provider_ et accessible dans ses descendants via `useContext` ❌

## 💻 J'utilise

### Un exemple personnel commenté  ✔️
```javascript
// Composant de login d'une application React
import React, { useState } from "react";
import { Formik, Form, Field } from "formik";
import { Link } from "react-router-dom";
import { FcGoogle } from "react-icons/fc";
import { CgFacebook } from "react-icons/cg";


import { defaulValuesLogin } from "../../shared/constants/formik-yup/default-values-form/idefaultValuesUser";
import { schemaFormLogin } from "../../shared/constants/formik-yup/yup/yupUser";
import {
  CustomCheckbox,
  CustomInput,
} from "../../shared/components/form-and-error-components/InputCustom";
import ErrorMessSmall from "./../../shared/components/form-and-error-components/ErrorMessSmall";
import { EyeIcon } from "@heroicons/react/solid";
import ReactFacebookLogin from "react-facebook-login";
import GoogleLogin from 'react-google-login';
import { URL_FORGOT_PASSWORD, URL_REGISTER } from "../../shared/constants/urls/urlConstants";

const LoginForm = ({
  submit,
  errorLog,
  hideModal,
  setViewPassword,
  viewPassword,
  googleSuccess,
  googleFailure,
  facebookSuccess
}) => (
  <Formik
    initialValues={defaulValuesLogin}
    validationSchema={schemaFormLogin}
    onSubmit={submit}
  >
    <Form className="flex flex-col mt-4">
      <div className="flex-col space-y-3">
        <div>
          <label htmlFor="firstname"> Adresse email </label>
          <Field
            type="text"
            name="email"
            placeholder="Entrez votre e-mail"
            component={CustomInput}
            className="lowercase"
          />
        </div>

        <div className="relative">
          <label htmlFor="password" className="mt-4">
            
            Votre mot de passe
          </label>
          <button type="button" onClick={() => setViewPassword(!viewPassword)}>
            <EyeIcon className="absolute h-6 w-6 top-8 right-3 z-50 text-gray-500 duration-200 hover:text-gray-700" />
          </button>
          <Field
            type={viewPassword ? "text" : "password" }
            name="password"
            placeholder="Mot de passe"
            component={CustomInput}
          />
        </div>
      </div>

      <div className="flex items-center justify-between my-4">
        <Field
          name="rememberMe"
          label="Se souvenir de moi"
          component={CustomCheckbox}
          value={true}
        />

        <Link
          to={URL_FORGOT_PASSWORD}
          className="text-sm font-medium text-primary-600 hover:text-primary-500 cursor-pointer"
        >
          Mot de passe oublié ?
        </Link>
      </div>

      <div className="flex flex-col self-center w-3/4 max-w-lg">
        <button type="submit" className="btn btn-yellow mb-2">
          Se connecter
        </button>

          <ReactFacebookLogin
              appId="458989835602531"
              autoLoad={true}
              fields="name,email"
              callback={facebookSuccess}
              cookie={false}
              language="fr_FR"
              cssClass="btn btn-blue mb-2 w-full"
              textButton=" Se connecter avec Facebook"
              icon={<CgFacebook className="mr-1"/>}
              />

            <GoogleLogin
              clientId="270509351999-4mof0jdh9v6shl96kf61d48mp1lg3d20.apps.googleusercontent.com"
              onSuccess={googleSuccess}
              onFailure={googleFailure}
              cookiePolicy={"single_host_origin"}
              render={renderProps => (
                <button onClick={renderProps.onClick}
                  disabled={renderProps.disabled}
                  className="flex content-center btn btn-white ml-0"><FcGoogle className="mt-auto mb-auto mr-1"/>
                  Se connecter avec Google
                </button>
              )}
              />


        {errorLog && (
          <ErrorMessSmall middle message="Login/Password incorrect(s)" />
        )}

        <p className="self-center mt-4 mb-1">vous êtes nouveau ici ?</p>

       
          <Link to={URL_REGISTER} 
          className="btn btn-yellow-border"
          onClick={() => hideModal(false)}>S'inscrire</Link>
        
      </div>
    </Form>
  </Formik>
);

const Login = (props) => {
  const [viewPassword, setViewPassword] = useState(false);


  return (
    <div className="p-3">
      <h2 className="my-5 text-2xl">Vous avez déjà un compte ?</h2>
      <LoginForm
        {...props}
        viewPassword={viewPassword}
        setViewPassword={setViewPassword}
      />
    </div>
  );
};

export default Login;
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
### Doc React
- https://fr.reactjs.org/

### Openclassroom
- https://openclassrooms.com/fr/courses/7008001-debutez-avec-react

## 🚧 Je franchis les obstacles

### Point de blocage  ✔️

Description:
- nécessite encore de la pratique pour les useRef, useLog et besoin de travailler le typage en typescript

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
