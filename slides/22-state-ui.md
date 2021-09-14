---
author: Colin A. Gross
title: BRAVO 2021
date: 2021-09-13
---
# Current State: UI
Moving to Vue

## ✓ Move Server Side Functions to API
## ✓ Simplify Build & Deploy
Previously:

1. build each vue component
1. copy all dist/ directories to flask assets
1. serve flask app

Currently:

```sh
npm run serve
```

## ◎ Consolidate Components
TODO: Migrate all .vue components under single application.
```sh
workspace/ui_bravo2/web_components/
├── bravo-model
│   ├── package.json
│   └── src
├── bravo-region
│   ├── package.json
│   └── src
├── bravo-search
│   ├── package.json
│   └── src
└── bravo-variant
    ├── package.json
    └── src
```

## ◎ Test Components
TODO: Verify expected appearance & behavior

```js
it("Horizontal rule gets centered", () => {
  expect(cmp.find(Message).attributes().style).toBe("padding-top: 10px;");
});

it('centers horizontal rule', () => {
  const wrapper = shallowMount(SearchBox, { props: { autofocus: true } })
  const hrStyle = wrapper.find('hr').attributes().style
  expect(hrStyle).to.include('margin-right: auto')
  expect(hrStyle).to.include('margin-left: auto')
})

```

