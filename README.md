## 測試 Select

### Select.test.js

```js
// Select.test.js

import React from 'react'
import { shallow, mount } from "enzyme";
import { findByTestAttr, checkProps } from '../../../test/testUtils';
import sinon from 'sinon';
import Select from '../Select'

const defaultProps = {}

const setup = (props = {}) => {
    const setupProps = { ...defaultProps, ...props }
    return shallow(<Select {...setupProps} />)
}


describe('select', () => {
    test('select, ', () => {
        const wrapper = setup()
        const w = findByTestAttr(wrapper, 'component-select')
        w.simulate('change', { target: { value: "two" } })
        expect(w.find('option').at(1).props().value).toBe("two")
    })
    test('select onChange ', () => {
        const wrapper = setup()
        const handleChangeSpy = sinon.spy();
        const w = findByTestAttr(wrapper, 'component-select')
        w.simulate('change', { target: { value: "two" } })
        setTimeout(() => {
            expect(handleChangeSpy.calledOnce).toBe(true);
        }, 1000)

    })
})
```
### Select.js

```js
// Select.js

import React, { Component } from 'react'
import PropTypes from 'prop-types'

class Select extends Component {
    constructor(props) {
        super(props)
    }
    handleChange = (e) => {
        console.log(e.target.value)
    }
    render() {
        return (
            <select data-test="component-select" onChange={e => this.handleChange(e)}>
                <option value="one">One</option>
                <option value="two">Two</option>
                <option value="three">Three</option>
            </select>
        )
    }
}

export default Select
```

### 執行測試

```
npm run test:coverage
```