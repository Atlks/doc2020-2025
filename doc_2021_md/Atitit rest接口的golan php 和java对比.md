Atitit rest接口的golan php 和java对比

Rest golan

//  rest

package main

import (
	"fmt"
	"html"
	"log"
	"net/http"
)

func main44() {
	fmt.Println(" start")
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		fmt.Fprintf(w, "Hello, %q", html.EscapeString(r.URL.Path))
	})

	http.HandleFunc("/a", func(w http.ResponseWriter, r *http.Request) {
		fmt.Fprintf(w, "Hello, aaaaa", html.EscapeString(r.URL.Path))
	})
	log.Fatal(http.ListenAndServe(":8080", nil))

	fmt.Println(" serivert ing..")
}


Php的更加路由简单，url文件夹一一对应
Java对springboot需要设定

