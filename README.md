### sessiongate-go 
---
https://github.com/f0rmiga/sessiongate-go


```go
// sessiongate_test.go

var signKey []byte

func init() {
  signKey = make([]byte, 16)
  rand.Read(signKey)
}

func TestInitializer(t *testing.T) {
  t.Run("should fail with missing SignKey", func(t *testing.T) {
    config := &Config{}
    
    _, err := NewSessiongate(config)
    if err == nil {
      t.Fail()
    }
  })
}

func TestStart(t *testing.T) {
  t.Run("Should fail with negative TTL", func(t *testing.T) {
    config := &Config{
      SignKey: signKey,
    }
    
    sesssiongate, err := NewSessiongate(config)
    if err != nil {
      t.Error(err)
    }
    
    _, err = sessiongate.Start(-1)
    if err == nil {
      t.Error(errors.New("Negative TTL should produce an error"))
    }
  })
  
  
}


```

```
```

```
```


