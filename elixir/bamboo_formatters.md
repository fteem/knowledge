# Bamboo - Formatting with Protocols

Another Elixir feature that Bamboo takes advantage of is protocols. Briefly, an
Elixir protocol is an interface that data can conform to, allowing for
polymorphism in our Elixir code.

In Bamboo, the Bamboo.Formatter defines an interface for converting data. For
[Hex.pm](https://github.com/hexpm/hex_web/pull/418/commits/3620ca8eb2fc08bdfa2f1a32ef098ffe1031d165)
, what I did was I created a formatter which will turn an instance of a
User struct into an email, so Bamboo can send the email to the correct email
addresses:

```elixir
defimpl Bamboo.Formatter, for: HexWeb.User do
  def format_email_address(user, _opts) do
    email = hd(user.emails).email

    {user.username, email}
  end
end
```
