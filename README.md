# Mouri (もURI)

A simple, easy to use, and relatively performant (see [benchmarks](#benchmarks)) way to create and join uri parts together.

Please note that this is not meant to handle many edge cases, and is meant and made for simple use cases.

# Usage
```js
import uri from 'mouri'

const API_URL = 'https://api.example.com/';

const userPostsUrl = (id, limit, offset) => {
  return uri`${API_URL}/users/${id}/posts/${{ limit: limit.toString(), offset: offset.toString() }}`
}

userPostsUrl("112233445566778899", 10, 5)
// => "https://api.example.com/users/112233445566778899/posts/limit=10&offset=5"
```

# Benchmarks

To run: `deno run .\bench.ts`

<!-- BENCHMARKS START -->
## Simple URL joining


pattern:
> `{API_URL}/users/{id}/posts/limit={limit}&offset={offset}`

expected result:
> `https://api.example.com/users/112233445566778899/posts/limit=10&offset=5`
            
|Name|Runs|Total (ms)|Average (ms)|
|:--|--:|--:|--:|
|mouri|1000|40.019|0.040|
|handwritten|1000|181.523|0.182|
|urlcat|1000|134.170|0.134|
<!-- BENCHMARKS END -->