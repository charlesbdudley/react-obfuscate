# react-obfuscate

[![npm version](https://badge.fury.io/js/react-obfuscate.svg)](https://www.npmjs.com/package/react-obfuscate)
[![npm](https://img.shields.io/npm/dm/react-obfuscate.svg)](https://www.npmjs.com/package/react-obfuscate)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://prettier.io)

![react-obfuscate](https://user-images.githubusercontent.com/7424180/28096225-c2f07142-666c-11e7-96ab-c12f34d1b86f.png)

## Demo & Examples

Live demo: [react-obfuscate.coston.io](https://react-obfuscate.coston.io)

## How it works

The user passes the contact link as an `email, tel, sms, or facetime` prop. The component obfuscates href data until an onClick event. Links are given their proper URL schemes (mailto, facetime, etc.) The link is rendered in reverse in the dom, but reversed again with css. This making the link useless for spammers, but user friendly on screen.

## Why

The world needs obfuscated links that display the link in a friendly way.

## Installation

```bash
npm install --save react-obfuscate
```

### Input

```js
import React from 'react'
import Obfuscate from 'react-obfuscate'

export default () => (
  <p>
    Phone: <Obfuscate tel="205-454-1234" />
    <br />
    Email:{' '}
    <Obfuscate
      email="coston.perkins@ua.edu"
      headers={{
        cc: 'dade@zero-cool.af',
        bcc: 'smith@machina.net',
        subject: 'react-obfuscate',
        body: 'Down with the machines!'
      }}
    />
  </p>
)
```

### Output

#### Robot Interaction

```html
<p>
  Phone: <a href="obfuscated" style="direction: rtl; unicode-bidi: bidi-override;">4321-454-502</a><br>
  Email: <a href="obfuscated" style="direction: rtl; unicode-bidi: bidi-override;">looc.notsoc@olleh</a>
</p>
```

#### Human Interaction

```js
<p>
  Phone: <a href="tel:205-454-1234">205-454-1234</a><br>
  Email: <a href="mailto:hello@coston.cool&subject=Question%20from%20the%20website&cc=friend@coston.cool">hello@coston.cool</a>
</p>
```

## Options

| Prop      | Type        | Argument     | Default      | Description                                                    |
| --------- | ----------- | ------------ | ------------ | -------------------------------------------------------------- |
| email     | `string`    | `<optional>` | `null`       | email address of the intended recipient                        |
| tel       | `string`    | `<optional>` | `null`       | telephone number of the intended recipient                     |
| sms       | `string`    | `<optional>` | `null`       | sms number of the intended recipient                           |
| facetime  | `string`    | `<optional>` | `null`       | facetime address of the intended recipient                     |
| headers   | `object`    | `<optional>` | `null`       | subject, cc, bcc, body, etc                                    |
| obfuscate | `boolean`   | `<optional>` | `true`       | set to false to disable obfuscation                            |
| linkText  | `string`    | `<optional>` | `obfuscated` | add custom obfuscated link text, like 'Email Me'               |
| element   | `string`    | `<optional>` | `'a'`        | custom element to render instead of an `a` tag                 |
| onClick   | `function`  | `<optional>` | `null`       | called prior to setting location (e.g. for analytics tracking) |

## Development

```bash
npm run dev
```

## Consecutive Obfuscate/inline elements
react-obfuscate is an inline element. Using consecutive inline elements inside a block element causes an issue with the `bidi-override` reversal on Chrome. To prevent this,
add any text between the elements, wrap `<Obfuscate/>` with another element (like `<span>`), or add `style={{display:'inline-block'}}` to prevent any issues.

Example Case:
```js
<address>
	<Obfuscate style={{display:'inline-block'}} email="-mail@mailbox.org" />
	<br />
	<Obfuscate style={{display:'inline-block'}} tel="+69 111 222 333" />
</address>
```

## Obfuscating custom elements with the `element` prop
With the `element` prop, users can obfuscate any element, like paragraphs or headers. Changing the dom element also removes the href and onClick props. Custom styling is required due to handling of right-to-left direction styles. Usually, adding `style={{textAlign:'left'}}` will suffice.

Example Case:
```js
<Obfuscate 
  element='p'
  style={{textAlign:'left'}}>
  This paragraph is more secret than others.
</Obfuscate>
```

## Contributors

react-obfuscate is awesome thanks to these community members:

* [coston](https://github.com/coston)
* [bostrom](https://github.com/bostrom)
* [timmygee](https://github.com/timmygee)
* [mic](https://github.com/mic)
* [ravinggenius](https://github.com/ravinggenius)

## Contributing

Please help make this react component better. Submit any issue and/or make a pull request!

## License

Licensed under the MIT license.
