# react-linkifier [![Build Status](https://travis-ci.org/pladaria/react-linkifier.svg)](https://travis-ci.org/pladaria/react-linkifier)

Tiny React library to extract URLs from a string and convert them to clickable links.
It will return an array of React components (anchors for links and spans por regular text).

- Very small (~1KB minified and gzipped)
- Use it as function or component
- Works great with complex URLs and handles many corner cases
- Allows custom props to be applied to &lt;a&gt; elements
- Automatically prepends `http://` to the href (or `mailto:` for emails)

## Install

```javascript
npm install --save react-linkifier
```

## Basic usage

### As component

```javascript
import Linkifier from 'react-linkifier';

const myComponent = () => (
    <Linkifier>
        check this: www.domain.com
    </Linkifier>
);

// Render result:
// <span>
//    <span>check this: </span><a href="http://www.domain.com">www.domain.com</a>
// </span>
```

### As function

```javascript
import {linkifier} from 'react-linkifier';

const myComponent = () => (
    <div>
        {linkifier('check this: www.domain.com')}
    </div>
);

// Render result:
// <div>
//     <span>check this: </span><a href="http://www.domain.com">www.domain.com</a>
// </div>
```

## Advanced usage

### As component

By default the Linkifier component wraps the children with a `span` element, you can override this using the `wrap` prop.

The class name is assigned to the wrapper.

```javascript
import Linkifier from 'react-linkifier';

const myComponent = () => (
    <Linkifier target="_blank" wrap="div" className="some-text">
        {'check this: www.domain.com'}
        <strong>send me a message: peter@domain.com</strong>
    </Linkifier>
);

// Render result:
// <div class="some-text">
//     <span>check this: </span><a target="_blank" href="http://www.domain.com">www.domain.com</a>
//     <strong>
//         <span>send me a message: </span>
//         <a target="_blank" href="mailto:peter@domain.com">peter@domain.com</a>
//     </strong>
// </div>
```

### As function

```javascript
import {linkifier} from 'react-linkifier';

const text = 'check this: www.domain.com';

const myComponent = () => (
    <div>
        {linkifier(text, {target: '_blank', key: 'k', className: 'link'})}
    </div>
);

// Render result:
// <div>
//     <span>check this: </span>
//     <a target="_blank" class="link" href="http://www.domain.com">www.domain.com</a>
// </div>
```

## License

MIT
