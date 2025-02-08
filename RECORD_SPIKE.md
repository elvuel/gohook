# RECORD_SPIKE


```go
func main() {
	hook.RecordWriter, _ = os.Create(fmt.Sprintf("recorder_%d.txt", time.Now().Unix()))

	defer hook.RecordWriter.Close()

	hook.Register(hook.KeyDown, []string{"]", "command"}, func(e hook.Event) {
		hook.RecordEnabled = !hook.RecordEnabled
		if hook.RecordEnabled {
			fmt.Println("Recording started")
		} else {
			fmt.Println("Recording stopped")
		}
	})

	s := hook.Start()
	<-hook.Process(s)
}
```