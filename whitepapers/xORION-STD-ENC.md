# xORION-STD-ENC
xORION-STD-ENC is an advanced algorithm designed by ORION'S CILOPS division. The algorithm is designed to
obfuscate machine code, preventing use by unauthorized parties.

## Description

The CILOPS team, while researching ways to remove `null` bytes from payloads, came up with away to obfuscate machine code by `xor`ing it with the first byte that doesn't exist in the payloads current bytes. The process starts with the value `255` and decrements by one until a valid value is found.

xORION-STD-ENC employs the technique, but only after its iterated through a key to secure the payload.

```
// pseudo code
key = 'bananas'
payload = '..removed..'

for letter in key {
  for byte, index in payload {
    payload[index] = byte xor key[letter].to_int
  }
}

final_encoder = 255
while payload.contains_byte(final_encoder) {
  final_encoder--
}

for byte, index in payload {
  payload[index] = byte xor final_encoder
}

```
