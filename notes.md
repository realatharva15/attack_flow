# Quick notes / Tips and Tricks:

`1.` if XSS is not possible by using <> symbols because they are HTML encoded in the response, create a user with the username `<script>alert('XSS')</script>` itself. the username is not getting HTML encoded and will result in an XSS vulnerability.

