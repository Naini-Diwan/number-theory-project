# A Number Theory Wonder

A browser-based text encoder/decoder built on modular exponentiation, the same core operation behind RSA encryption. Pick a key and a modulus, and the tool turns your text into a string of numbers and back again. I built this tool using HTML, based on my learnings during the Reading Project in *Number Theory* under the supervision of **Dr. Ajit Bhand** [Dept. of Mathematics, IISER Bhopal]. 

## How it works

Each character in your text has a numeric code (its ASCII/Unicode value). Encoding raises that code to the power of your key `k`, then takes the result modulo `m`:

```
encoded = (char_code ^ k) mod m
```

Decoding reverses this using modular inverse arithmetic, turning the numbers back into the original characters. For this to work reliably, `m` must be prime and `k` must be coprime to `m - 1`. The tool checks both automatically and tells you if your chosen key/modulus pair won't round-trip cleanly.

## Using the site

1. **Open the [`website`](https://naini-diwan.github.io/number-theory-project/)** in any browser. No installation or server is needed, it runs entirely client-side.
2. **Type or paste your text** into the "Text" box.
3. **Set your Key (k)** — this is your encoding exponent. Default is `3`.
4. **Set your Modulus (m)** — this must be a prime number. Default is `257`.
5. Click **Encode** to turn your text into a space-separated string of numbers.
6. To reverse it, paste that number string back into the "Text" box and click **Decode**.

The Result box shows the output, and the status line beneath it tells you whether the operation completed cleanly or ran into issues.

### Note

- **"Modulus (m) must be prime"** — pick a prime number (e.g. 257, 251, 263). Non-prime moduli break the math that makes decoding reversible.
- **"Key (k) must be coprime to m-1"** — some keys don't have a valid inverse for a given modulus. The error message shows you the conflicting `gcd` value; try a different `k`.
- **Characters flagged as out of range during encode** — your modulus is too small to represent every character in your text. Increase `m` (and make sure it's still prime).

### Good starter values

| k | m | Notes |
|---|---|---|
| 3 | 257 | Default. Works for standard Latin-1 text. |
| 5 | 257 | Also valid, produces different output. |
| 3 | 65537 | Larger modulus, supports a much wider character range. |

## Why it's "a number theory wonder"

The same modular exponentiation trick, raising a number to a power and reducing modulo a prime, is the mathematical backbone of RSA public-key cryptography. This tool is a simplified, single-key (symmetric) illustration of that idea: encode with `k`, decode with its modular inverse, both anchored to the same prime modulus. 

I hope you have fun exploring it! Do let me know if you have any questions or suggestions.

© 2025 [Naini Diwan](https://naini-diwan.github.io/Hello-Naini/). All Rights Reserved.
