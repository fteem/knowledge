# Bamboo/Config

## SMTP Adapter
- The port number always [has](https://github.com/fewlinesco/bamboo_smtp/blob/develop/lib/bamboo/adapters/smtp_adapter.ex#L304-L306) [to be an](https://github.com/Vagabond/gen_smtp/blob/37cc4bdf2489ca178af2113b0eea4533d6a3fa4d/src/gen_smtp_client.erl#L523) [integer](https://github.com/hexpm/hex_web/pull/418/commits/2c1690c78cc19d972efd14ab58bdccc23d880000), otherwise `gen_smtp` will try to connect to [port 25](https://github.com/Vagabond/gen_smtp/blob/37cc4bdf2489ca178af2113b0eea4533d6a3fa4d/src/gen_smtp_client.erl#L526).
