# jester
[![CircleCI Status](https://circleci.com/gh/scotiabank/jester.svg?style=shield&circle-token=:circle-token)](https://circleci.com/gh/scotiabank/jester)

Jester DRYs up your Jest + React snapshot code.

## Why use jester?

Jester React will reduce the amount of boilerplate you write significantly.

Example without jester:

```js
import { Header, Paragraph } from './components';
import { shallow } from 'enzyme';
import toJSON from 'enzyme-to-json';

describe('components', () => {
  test('header should match snapshot', () => {
    const tree = toJson(shallow(<Header />));
    expect(tree).toMatchSnapshot();
  });
  test('paragraph should match snapshot', () => {
    const tree = toJson(shallow(<Paragraph />));
    expect(tree).toMatchSnapshot();
  });
});
```
Example with jester:

```js
import * as Components from './components';
import jester from '@scotia/jester-react';

describe('shallow', () => {
  jester.runShallowSnapshotTests(Components);
});
```

As you can see for each component that is added the more boilerplate code jester saves you (about 4 lines per component).


## Packages

This repository is a monorepo. That means we publih multiple npm packages from the same codebase, such as:

| Package | Description |
|---------|-------------|
| [`jester`](/packages/jester) | The basic version for creating snapshots with plain JSON |
| [`jester-react`](/packages/jester-react) |  The React specific version for use with React Components|