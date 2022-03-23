---
description: >-
  This page provides a list of the browser resolution test domains and reviews
  the process for retrieving test records.
---

# Browser Resolution Test Domains

| Domain name |
| :--- |
| udtestdev-dns-ipfs.crypto |
| udtestdev-dns.crypto |
| udtestdev-dns-a-record.crypto |
| udtestdev-ipfs.crypto |
| udtestdev-dns-global-ttl.crypto |
| udtestdev-dns-ipfs-no-preffered-records.crypto |
| udtestdev-dns-cname.crypto |
| udtestdev-dns-ipfs-redirect.crypto |
| udtestdev-redirect.crypto |
| udtestdev-dns-ipfs-redirect-legacy-ipfs-legacy.crypto |
| udtestdev-ipfs-legacy.crypto |
| udtestdev-ipfs-legacy-redirect-legacy.crypto |
| udtestdev-redirect-legacy.crypto |

## Getting test records

{% tabs %}
{% tab title="resolution-js" %}
Check records with [resolution-js](https://github.com/unstoppabledomains/resolution) library:

```typescript
import Resolution from '@unstoppabledomains/resolution/build/Resolution';

const resolution = new Resolution();
resolution.allRecords('udtestdev-dns-ipfs.crypto').then((records) => {
  console.log(records);
  // Output
  // {
  //   'dns.A': '["10.0.0.1","10.0.0.2"]',
  //   'dns.A.ttl': '1800',
  //   'dns.ttl': '1000',
  //   'dns.CNAME': '',
  //   'dns.CNAME.ttl': '',
  //   'dweb.ipfs.hash': 'QmVJ26hBrwwNAPVmLavEFXDUunNDXeFSeMPmHuPxKe6dJv',
  //   'browser.preferred_protocols': '["ipfs","https","http"]',
  //   'browser.redirect_url': '',
  //   'ipfs.html.value': '',
  //   'ipfs.redirect_domain.value': ''
  // }
});
```
{% endtab %}

{% tab title="resolution-js CLI" %}
Check records with [resolution-js CLI](https://github.com/unstoppabledomains/resolution#command-line-interface):

```bash
$ resolution -d udtestdev-dns-ipfs.crypto -a
{
    "records": {
        "dns.A": "[\"10.0.0.1\",\"10.0.0.2\"]",
        "dns.A.ttl": "1800",
        "dns.ttl": "1000",
        "dweb.ipfs.hash": "QmVJ26hBrwwNAPVmLavEFXDUunNDXeFSeMPmHuPxKe6dJv",
        "browser.preferred_protocols": "[\"ipfs\",\"https\",\"http\"]"
    }
}
```
{% endtab %}

{% tab title="resolution-swift" %}
Check records with [resolution-swift](https://github.com/unstoppabledomains/resolution-swift) library:

```swift
import UnstoppableDomainsResolution

guard let resolution = try? Resolution() else {
  print ("Init of Resolution instance with default parameters failed...")
  return
}

resolution.allRecords(domain: "udtestdev-dns-ipfs.crypto") { result in
  switch result {
  case .success(let returnValue):
    dump(returnValue);
     /*
        Output:
        'dns.A': '["10.0.0.1","10.0.0.2"]'
        'dns.A.ttl': '1800'
        'dns.ttl': '1000'
        'dns.CNAME': ''
        'dns.CNAME.ttl': ''
        'dweb.ipfs.hash': 'QmVJ26hBrwwNAPVmLavEFXDUunNDXeFSeMPmHuPxKe6dJv'
        'browser.preferred_protocols': '["ipfs","https","http"]'
        'browser.redirect_url': ''
        'ipfs.html.value': '',
        'ipfs.redirect_domain.value': ''
      */
  case .failure(let error):
    XCTFail("Expected all records from uns domain, but got \(error)");
  }
}
```
{% endtab %}

{% tab title="resolution-java" %}
Check records with [resolution-java](https://github.com/unstoppabledomains/resolution-java) library:

```java
import com.unstoppabledomains.resolution.Resolution;
import java.util.Map;
​
public class Main {
  public static void main(String[] args) {
    try {
      Resolution res = new Resolution();
      Map<String, String> records = res.getAllRecords("udtestdev-dns-ipfs.crypto");
      for (Map.Entry<String, String> entry : records.entrySet()) {
        System.out.println(String.format("'%s': '%s'", entry.getKey(), entry.getValue());
      }
     /*
      * Output:
      * 'dns.A': '["10.0.0.1","10.0.0.2"]'
      * 'dns.A.ttl': '1800'
      * 'dns.ttl': '1000'
      * 'dns.CNAME': ''
      * 'dns.CNAME.ttl': ''
      * 'dweb.ipfs.hash': 'QmVJ26hBrwwNAPVmLavEFXDUunNDXeFSeMPmHuPxKe6dJv'
      * 'browser.preferred_protocols': '["ipfs","https","http"]'
      * 'browser.redirect_url': ''
      * 'ipfs.html.value': '',
      * 'ipfs.redirect_domain.value': ''
      */
    } catch (Exception e) {
      e.printStackTrace();
    }
  }
}
```
{% endtab %}

{% tab title="resolution-go" %}
Check records with [resolution-go](https://github.com/unstoppabledomains/resolution-go) library:

```go
package main
​
import (
  "fmt"
  "github.com/unstoppabledomains/resolution-go"
)
​
func main() {
  uns, _ := resolution.NewUnsBuilder().Build()
  allUnsRecords, _ := uns.AllRecords("udtestdev-dns-ipfs.crypto")
  fmt.Println("Records for udtestdev-dns-ipfs.crypto", allUnsRecords)
  // Output
  // {
  //   'dns.A': '["10.0.0.1","10.0.0.2"]',
  //   'dns.A.ttl': '1800',
  //   'dns.ttl': '1000',
  //   'dns.CNAME': '',
  //   'dns.CNAME.ttl': '',
  //   'dweb.ipfs.hash': 'QmVJ26hBrwwNAPVmLavEFXDUunNDXeFSeMPmHuPxKe6dJv',
  //   'browser.preferred_protocols': '["ipfs","https","http"]',
  //   'browser.redirect_url': '',
  //   'ipfs.html.value': '',
  //   'ipfs.redirect_domain.value': ''
  // }
}
```
{% endtab %}
{% endtabs %}
