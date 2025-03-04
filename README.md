# God 神

### Installation

```
$ go get github.com/dongri/god
```

### Detect Credit Card Type
```go
package main
import (
	"fmt"
	"github.com/dongri/god"
)
func main() {
	cardType1 := god.DetectCardType("4111111111111")
	fmt.Println(cardType1) // Visa
	cardType2 := god.DetectCardType("5555555555554444")
	fmt.Println(cardType2) // Master
}
```

### Date Format
```go
package main
import (
	"fmt"
	"time"
	"github.com/dongri/god"
)
func main() {
	time, _ := time.Parse("2006-01-02 15:04:05", "2015-03-04 23:29:23")
	formatedDate := god.DateFormat(time, "%Y年%m月%d日 %H時%M分%S秒")
	fmt.Println(formatedDate) // 2015年03月04日 23時29分23秒
}
```

### Random
```go
package main
import (
	"fmt"
	"github.com/dongri/god"
)
func main() {
	random := new(god.Random)
	random.UseNumber()
	random.UseSmallLetter()
	random.UseCapitalLetter()
	r := random.Random(20)
	fmt.Println(r) // 6Zyk2vOQYNIKmbIa6BcH
}
```

### Sha1
```go
package main
import (
	"fmt"
	"github.com/dongri/god"
)
func main() {
	s := god.Sha512Sum512("hello"))
	fmt.Println(s)
}
```

### Cipher
```go
package main
import (
	"fmt"
	"github.com/dongri/god"
)
func main() {
	encryptedText, err := god.EncryptString("passwordpasswordpasswordpassword", "hoge")
	fmt.Println(err, encryptedText)
}
```

### Beacon
```go
package main
import (
	"fmt"
	"github.com/dongri/god"
)
func main() {
	major, minor := god.PackBeacon(1,2,8)
	fmt.Println(major, minor)

	major, minor := god.UnpackBeacon(0, 258,8)
	fmt.Println(major, minor)
}
```

### Int min, max
```go
package main
import (
	"fmt"
	"github.com/dongri/god"
)
func main() {
	max := god.MaxOf(4, 6, 9, 7, 2, 1, 8)
	fmt.Println(max) // 9
}
```

### Replace hyphen
```go
package main
import (
	"fmt"
	"github.com/dongri/god"
)
func main() {
	result := god.ReplaceHyphen("test-testーテスト█测试▬테스트", HANKAKU_HYPHEN)
	fmt.Println(result) // test-test-テスト-测试-테스트
}
```

### Replace wave dash
```go
package main
import (
	"fmt"
	"github.com/dongri/god"
)
func main() {
	result := god.ReplaceWaveDash("test῀test∼テスト～测试〜테스트")
	fmt.Println(result) // test~test~テスト~测试~테스트
}
```

### Caesar Cipher
```go
package main
import (
	"fmt"
	"github.com/dongri/god"
)

func main() {
	caesarCipher := god.NewCaesarCipher(3)
	encrypted := caesarCipher.Encrypt("hello")
	fmt.Println(encrypted) // khoor
}
```

# License

The MIT License (MIT)

Copyright (c) 2015 Dongri Jin

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
