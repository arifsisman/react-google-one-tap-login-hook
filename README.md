# React Google One Tap Login Hook

A plug and play React hook used for Google One Tap Login

 <p align="center">
  <img height="300" src="https://user-images.githubusercontent.com/18334319/112712466-d8707800-8ee0-11eb-940f-7aa9b5fe7fac.png">
</p>

## Usage

```ts
  useGoogleOneTapLogin({
    client_id: <your-google-client-id>,
    disabled: false,
    callback: ({ credential }) => {
        // credential is ID Token
    }
  });
```

Note that

- credential response is **ID Token** and can be used for signIn to Firebase or authenticate any other server which accepts Google Login.
- disabled parameter is **optional**, in case of you want to disable hook on some condition.
- For Google Documentation of Google Sign In -> https://developers.google.com/identity/gsi/web
- For all parameters of IdConfiguration -> https://developers.google.com/identity/gsi/web/reference/js-reference#IdConfiguration
- You can also find useScript hook at https://usehooks.com/useScript

## Firebase SignIn with Credential Example

```ts
  useGoogleOneTapLogin({
    client_id: <your-google-client-id>,
    disabled: user !== null,
    callback: ({ credential }) => {
      const OAuthCredential = firebase.auth.GoogleAuthProvider.credential(credential);
      firebase.auth().signInWithCredential(OAuthCredential)
    }
  });
```
