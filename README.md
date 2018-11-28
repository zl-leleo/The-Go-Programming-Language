

// 读取url中的参数
func main() {
	http.HandleFunc("/", func(writer http.ResponseWriter, request *http.Request) {
		fmt.Fprintf(writer, "<h1>hello world %s !</h1>", request.FormValue("name"))
	})
	http.ListenAndServe(":8888", nil)
}

// 多线程并发
func main(){
	ch := make(chan string)
	for i :=0; i < 5000; i++ {
		// go starts a goroutine
		go printHelloWorld(i, ch)
	}
	for {
		msg := <- ch
		fmt.Println(msg)
	}
}
func printHelloWorld(i int, ch chan string)  {
	for {
		ch <- fmt.Sprintf("Hello world form " + "goroutime %d !\n", i)
	}
}

// 内部排序实例
func main(){
	// Creates a slice if int
	a := []int{3,6,4,85,4,6,4,9,10}
	sort.Ints(a)

	for i, v := range a {
		fmt.Println(i, v)
	}

	// 如果不想输出i，把i换成下划线_
	//for _, v := range a {
	//	fmt.Println(v)
	//}
}

// 归并排序算法

