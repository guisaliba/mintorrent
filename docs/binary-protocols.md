# binary protocols

these are machine-optimized protocols. while HTTP is a human-readable protocol, they're not as friendly to machines as they're to humans.
for that, binary protocols exist. instead of reading something verbose, friendly, that you can even debug with `curl` you'd have just bytes.

that's really meant to be: `Content-Length: 42` is an usual header for HTTP's request-response lifecycle, binary protocols would simply
write that as 4 raw bytes representing the integer 42 directly in memory. no ASCII digits, nothing. just `\x00\x00\x00\x2a`.

the BitTorrent peer write protocol is a binary. a message looks like:
`[4 bytes: length] [1 byte: message type] [payload ...]

a byte represents the message type, not a word. it straight tells e.g.: "this is a REQUEST message" but with bytes, not lines.

Bencode (BItTorrent's serialization format) is a hybrid. it's ASCII-readable with some binary thinking.
