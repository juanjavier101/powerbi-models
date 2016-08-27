# powerbi-models
[![Build Status](https://img.shields.io/travis/Microsoft/powerbi-models.svg)](https://travis-ci.org/Microsoft/powerbi-models)
[![NPM Version](https://img.shields.io/npm/v/powerbi-models.svg)](https://www.npmjs.com/package/powerbi-models)
[![NPM Total Downloads](https://img.shields.io/npm/dt/powerbi-models.svg)](https://www.npmjs.com/package/powerbi-models)
[![NPM Monthly Downloads](https://img.shields.io/npm/dm/powerbi-models.svg)](https://www.npmjs.com/package/powerbi-models)
[![GitHub tag](https://img.shields.io/github/tag/microsoft/powerbi-models.svg)](https://github.com/Microsoft/powerbi-models/tags)

Contains JavaScript &amp; TypeScript object models for Microsoft Power BI JavaScript SDK.

For each model there is a TypeScript interface, a json schema definitions, and a validation function to ensure a given object is a valid model.

## Documentation
### [https://microsoft.github.io/powerbi-models](https://microsoft.github.io/powerbi-models)

## Getting Started

Install

```bash
npm install --save powerbi-models
```

Import

```typescript
import * as models from 'powerbi-models';
```

Usage

Validation:

```typescript
let testObject = { x: 1 };

const errors = models.validateLoad(testObject);

if(errors) {
  console.warn(errors);
}

```
Would output to the console:

```typescript
[
  {
    message: 'accessToken is required'
  }
]
```

Creating filters:
```typescript
const basicFilter: models.IBasicFilter = {
  target: {
    table: "Products",
    column: "Version"
  },
  operator: "In",
  values: [
    1,
    2,
    3,
    4
  ]
};

const advancedFilter: models.IAdvancedFilter = {
  target: {
    table: "Products",
    column: "Name"
  },
  logicalOperator: "Or",
  conditions: [
    {
      operator: "Contains",
      value: "Power"
    },
    {
      operator: "Contains",
      value: "Microsoft"
    }
  ]
};
```

Or use the constructor methods:
```typescript
const advancedFilter = new models.AdvancedFilter(
  {
    table: "Products",
    column: "Name"
  },
  "Or",
  {
    operator: "Contains",
    value: "Power"
  },
  {
    operator: "Contains",
    value: "Microsoft"
  }
);
```