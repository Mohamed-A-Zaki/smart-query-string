# Smart Query String

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![npm version](https://img.shields.io/badge/npm-v1.0.0-blue)](https://www.npmjs.com/package/smart-query-string)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)

A lightweight, zero-dependency TypeScript utility for parsing and manipulating URL query strings. This package provides
a simple and type-safe API for working with URL query parameters in both browser and Node.js environments.

## Features

- 🌐 First-class browser support with direct URL manipulation
- 🔍 Parse query strings into JavaScript objects
- 📝 Stringify objects into query strings
- 🔄 Support for arrays and nested objects
- 🛠️ Built-in TypeScript support
- 🚫 Zero dependencies
- 📦 Small bundle size

## Installation

### Using npm

```bash
npm install smart-query-string
```

### Using Yarn

```bash
yarn add smart-query-string
```

### Using pnpm

```bash
pnpm add smart-query-string
```

> **Framework Agnostic**
> This package is designed to work seamlessly with any JavaScript framework including React, Vue, Angular, Svelte, and
> more. It has no framework dependencies and can be used in any JavaScript or TypeScript project.

## Browser Usage

### Get Current Query Parameters

```typescript
import {queryString} from 'smart-query-string';

// Get all current URL query parameters as an object
const currentParams = queryString.get();
// If URL is https://example.com?page=1&sort=name
// Returns: { page: '1', sort: 'name' }
```

### Set Query Parameters

```typescript
import {queryString} from 'smart-query-string';

// Set query parameters (replaces all existing ones)
queryString.set({page: 2, sort: 'name'});
// Updates URL to: https://example.com?page=2&sort=name
```

### Update Specific Parameters

```typescript
import {queryString} from 'smart-query-string';

// Update specific parameters while preserving others
queryString.update({page: 3});
// If current URL is https://example.com?page=2&sort=name
// Updates to: https://example.com?page=3&sort=name
```

### Remove All Query Parameters

```typescript
import {queryString} from 'smart-query-string';

// Remove all query parameters from the URL
queryString.remove();
// Updates URL to: https://example.com
```

### Remove Specific Parameters

```typescript
import {queryString} from 'smart-query-string';

// Remove specific query parameters
queryString.removeKeys(['sort', 'filter']);
// If current URL is https://example.com?page=1&sort=name&filter=active
// Updates to: https://example.com?page=1
```

## General Usage

### Parsing Query Strings

```typescript
import {queryString} from 'smart-query-string';

// Parse a query string
const params = queryString.parse('foo=bar&baz=qux');
// Returns: { foo: 'bar', baz: 'qux' }

// Parse URL with query string
const {url, query} = queryString.parseUrl('https://example.com?foo=bar');
// url: 'https://example.com'
// query: { foo: 'bar' }
```

### Stringifying Objects

```typescript
import {queryString} from 'smart-query-string';

// Stringify an object
const query = queryString.stringify({foo: 'bar', baz: 'qux'});
// Returns: 'foo=bar&baz=qux'

// Stringify with URL
const url = queryString.stringifyUrl({
  url: 'https://example.com',
  query: {foo: 'bar'}
});
// Returns: 'https://example.com?foo=bar'
```

## TypeScript Support

This package is written in TypeScript and includes type definitions out of the box.

## License

MIT © [Mohamed Zaki](https://github.com/Mohamed-A-Zaki)
