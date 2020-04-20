# Signing API requests

**Key generation**

The client on his side generates a public and private key based on the RSA256 algorithm. After that it sends only the public key to [eugene@cryptoprocessing.io](mailto:eugene@cryptoprocessing.io), this key will be used to validate all requests. Unsigned requests will be rejected.


**Create request signature**

Sample code for creating a signature:

<div class="center-column"></div>
```ruby
Base64.strict_encode64(OpenSSL::PKey::RSA.new(YOUR_PRIVATE_KEY).private_encrypt(Digest::SHA256.hexdigest("#{API_KEY}#{URL}#{BODY_STR}")))
```
<br/>
The signature is added to the Sign header of the request.

Sample code to add a Sign header:

<div class="center-column"></div>
```ruby
post URL, params: JSON.load(BODY_STR), as: :json, headers: {
  "Content-Type": "application/json",
  "Authorization": "Token #{API_KEY}",
  "Sign": Base64.strict_encode64(OpenSSL::PKey::RSA.new(YOUR_PRIVATE_KEY).private_encrypt(Digest::SHA256.hexdigest("#{API_KEY}#{URL}#{BODY_STR}")))
}
```
<br/>
  
Variable | Meaning
---------- | -------
YOUR_PRIVATE_KEY | private key
API_KEY | key generated in your account 
URL | request URL (for example, https://cryptoprocessing.io/api/v1/ping)
BODY_STR | request body, if any
