## 測試 SnapShot

### SnapShot.test.js

```js
// SnapShot.test.js

import React from 'react'
import { shallow, mount } from "enzyme";
import { findByTestAttr, checkProps } from '../../../test/testUtils';
import sinon from 'sinon';
import SnapShot from '../SnapShot'

const defaultProps = {}

const setup = (props = {}) => {
    const setupProps = { ...defaultProps, ...props }
    return shallow(<SnapShot {...setupProps} />)
}

describe('props function', () => {
    test('render a label', () => {
        const wrapper = setup()
        expect(wrapper).toMatchSnapshot();
    })
})

```
### SnapShot.js

```js

// SnapShot.js
import React, { Component } from 'react'
import PropTypes from 'prop-types'

class SnapShot extends Component {
    constructor(props) {
        super(props)
    }
    render() {
        return (
            <div>
                <h1>title</h1>
                <p>123</p>
            </div>
        )
    }
}

export default SnapShot
```

### 執行測試

```
npm run test:coverage
```