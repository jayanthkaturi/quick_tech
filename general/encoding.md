### Encoding/Unicode Python 2.x World

```
Raw string in bits with <previuously_known_encoding> (\x80 Euro in cp1252)
    -> decoder (decoder_map) -> Unicode Representation (\u20AC for Euro)

Unicode Representation (\u20AC for Euro) -> encoder (encoder_map)
    -> Raw string bits in <encoder_map> encoding> (\xe2\x82\xac Euro in UTF-8)
```
