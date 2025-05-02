# Ascent.encode

### Ascent.encode - Data Encoding Methods

#### Apica.encode.base64

Encodes a string in Base64 format.

<pre class="language-go"><code class="lang-go"><strong>ascent.encode.b64(input:string) : string;
</strong></code></pre>

| Parameter | Type   | Description    |
| --------- | ------ | -------------- |
| srting    | string | Value to enode |

Examples

To base64-encode the username

```
ascent.encode.b64("Username")
```

#### Ascent.encode.gzip

Compress a string using Gzip. Output a base64 encode string

```
ascent.encode.gzip(input: string): string;
```

| Parameter | Type   | Description     |
| --------- | ------ | --------------- |
| string    | string | Value to encode |

Examples

To encode the username

```
Event.encode = ascent.encode.b64("Username");
```

#### Ascent.encode.uri

Encodes a string using URI encoding

```
ascent.encode.uri(input: string): string;
```

| Parameter | Type   | Description     |
| --------- | ------ | --------------- |
| string    | string | Value to encode |

Examples

To encode the username

```
Event.encode = ascent.encode.uri("Username");
```

#### Ascent.encode.hex

Encodes a string in Hexadecimal format.

```
ascent.encode.hex(input: string): string
```

| Parameter | Type                                      | Description     |
| --------- | ----------------------------------------- | --------------- |
| string    | <mark style="color:yellow;">string</mark> | Value to encode |

Examples

To encode the username

```
Event.encode =  ascent.encode.hex("Username");
```
