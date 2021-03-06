---
path: '/materials/relay-sink'
type: 'GitHub'
img: './screenshot.png'
material:
  title: 'relay-sink'
  url: 'https://github.com/acdlite/relay-sink'
  github_url: 'https://github.com/acdlite/relay-sink'
  subscribers_count: '2'
  stargazers_count: '128'
  tags: ['']
  subtitle: 'Use Relay to fetch and store data outside of a React component'
  clone_url: 'https://github.com/acdlite/relay-sink.git'
  ssh_url: 'git@github.com:acdlite/relay-sink.git'
  pushed_at: '2017-06-19T15:46:13Z'
  updated_at: '2018-12-23T00:44:23Z'
  author:
    name: 'acdlite'
    avatar: 'https://avatars0.githubusercontent.com/u/3624098?v=4'
    github_url: 'https://github.com/acdlite'
  latestRelease:
    tag_name: null
    name: null
    url: null
    created_at: null
---
relay-sink
----------

[![build status](https://img.shields.io/travis/acdlite/relay-sink/master.svg?style=flat-square)](https://travis-ci.org/acdlite/relay-sink)
[![npm version](https://img.shields.io/npm/v/relay-sink.svg?style=flat-square)](https://www.npmjs.com/package/relay-sink)

## Usage

```js
import { createSink } from 'relay-sink';

const TyrionSink = createSink({
  // Normal Relay Container configuration
  fragments: {
    tyrion: () => Relay.QL`
      fragment on Character {
        name,
        house
      }
    `
  }
});

// A sink is a Relay Container. Compose with parent Relay containers like
// normal. Note that `this.props.tyrion` and `fragments.tyrion` below are not
// the same value — the former points to a value inside Relay's global store,
// while the latter is the actual unwrapped data.
<TyrionSink tyrion={this.props.tyrion} onFragmentUpdate={fragments => {
  expect(fragments.tyrion.name).to.equal('Tyrion');
  expect(fragments.tyrion.house).to.equal('Lannister');

  // Do whatever you want with the data — e.g. dispatch it to a Flux store
  store.dispatch({
    type: UPDATE_TYRION,
    payload: fragments.tyrion
  });
}}/>
```
