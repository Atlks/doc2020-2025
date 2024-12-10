async functions and the top level bodies of modules


await#1模块中的顶层
您可以await在模块的顶层使用。
MJS文件模式


#2 - 永不拒绝的顶级async函数


(async () => {
    const text = await main();
    console.log(text);
})().catch(e => {
    // Deal with the fact the chain failed
});



#3 -then和catch
main()
    .then(text => {
        console.log(text);
    })
    .catch(err => {
        // Deal with the fact the chain failed
    });

