# Smart Query String

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![npm version](https://img.shields.io/badge/npm-v1.0.0-blue)](https://www.npmjs.com/package/smart-query-string)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)

A lightweight, zero-dependency TypeScript utility for parsing and manipulating URL query strings. This package provides a simple and type-safe API for working with URL query parameters in both browser and Node.js environments.

## Features

- 🔍 Parse query strings into JavaScript objects
- 📝 Stringify objects into query strings
- 🔄 Support for arrays and nested objects
- 🛠️ Built-in TypeScript support
- 🚫 Zero dependencies
- 🌐 Works in both browser and Node.js environments
- 📦 Small bundle size

## Installation

```bash
npm install smart-query-string
# or
yarn add smart-query-string
# or
pnpm add smart-query-string
```

## Usage

### Basic Parsing

```typescript
import { queryString } from 'smart-query-string';

// Parse a query string
const params = queryString.parse('foo=bar&baz=qux');
// { foo: 'bar', baz: 'qux' }

// Parse URL with query string
const { url, query } = queryString.parseUrl('https://example.com?foo=bar');
// url: 'https://example.com'
// query: { foo: 'bar' }
```

### Stringifying Objects

```typescript
import { queryString } from 'smart-query-string';

// Stringify an object
const query = queryString.stringify({ foo: 'bar', baz: 'qux' });
// 'foo=bar&baz=qux'

// Stringify with URL
const url = queryString.stringifyUrl({
  url: 'https://example.com',
  query: { foo: 'bar' }
});
// 'https://example.com?foo=bar'
```

### Browser Usage

```typescript
import { queryString } from 'smart-query-string';

// Get current URL query parameters
const currentParams = queryString.get();

// Update query parameters
queryString.set({ page: 2, sort: 'name' });

// Update specific parameters while preserving others
queryString.update({ page: 3 });

// Remove all query parameters
queryString.remove();

// Remove specific parameters
queryString.removeKeys(['sort', 'filter']);
```

## API Reference

### `parse(queryString: string, options?: ParseOptions): QueryObject`

Parses a query string into an object.

### `stringify(obj: QueryObject, options?: StringifyOptions): string`

Stringifies an object into a query string.

### `parseUrl(url: string, options?: ParseOptions): { url: string; query: QueryObject }`

Extracts and parses the query string from a URL.

### `stringifyUrl(input: { url: string; query?: QueryObject }, options?: StringifyOptions): string`

Stringifies an object into a query string and appends it to a URL.

### `get(options?: ParseOptions): QueryObject`

Gets the current URL's query parameters (browser only).

### `set(query: QueryObject, options?: StringifyOptions): void`

Sets the browser's URL query parameters (browser only).

### `update(updates: QueryObject, options?: StringifyOptions): void`

Updates the browser's URL query parameters while preserving existing ones (browser only).

### `remove(): void`

Removes all query parameters from the URL (browser only).

### `removeKeys(keys: string[], options?: StringifyOptions): void`

Removes specific query parameters from the URL (browser only).

## Options

### ParseOptions

- `decode` (boolean, default: `true`): Whether to decode the query string values.
- `arrayFormat` ('none' | 'bracket' | 'index' | 'comma', default: 'none'): How to handle arrays in the query string.
  - `'none'`: `foo=1&foo=2` → `{ foo: ['1', '2'] }`
  - `'bracket'`: `foo[]=1&foo[]=2` → `{ foo: ['1', '2'] }`
  - `'index'`: `foo[0]=1&foo[1]=2` → `{ foo: ['1', '2'] }`
  - `'comma'`: `foo=1,2` → `{ foo: ['1', '2'] }`

### StringifyOptions

- `encode` (boolean, default: `true`): Whether to encode the query string values.
- `arrayFormat` ('none' | 'bracket' | 'index' | 'comma', default: 'none'): How to handle arrays in the query string.
- `skipNull` (boolean, default: `true`): Whether to skip null values.
- `skipEmptyString` (boolean, default: `true`): Whether to skip empty strings.

## TypeScript Support

This package is written in TypeScript and includes type definitions out of the box.

## License

MIT © [Mohamed Zaki](https://github.com/Mohamed-A-Zaki)
