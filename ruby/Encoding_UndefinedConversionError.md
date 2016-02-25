###Encoding::UndefinedConversionError: "\xFF" from ASCII-8BIT to UTF-8

According Rails 4.1 release note:

```
    Removed support for the encode_json hook used for encoding custom objects into JSON. This feature has been extracted into the activesupport-json_encoder gem. (Related Pull Request / More Details)

```

Because activesupport doesn't encoding invalid code anymore. Add activesupport-json_encoder gem to Gemfile fix this issue.

Link: [carrierwave upload Encoding::UndefinedConversionError: “\xFF” from ASCII-8BIT to UTF-8](http://stackoverflow.com/questions/24164205/carrierwave-upload-encodingundefinedconversionerror-xff-from-ascii-8bit-to)

