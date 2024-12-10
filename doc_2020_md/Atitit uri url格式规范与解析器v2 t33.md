Atitit uri url格式规范与解析器 .URIparser

/bookmarksHtmlEverythingIndexPrj/src/com/attilax/net/URIparser.java


默认的uri解析器存在bug，，如果密码里面存在金号则解析出错。。

 "http://root: 132.148.11:22";

所以需要自己写了。
        void parse(boolean rsa) throws URISyntaxException {
方法后面添加
              
            String[] aStrings=this.input.split("@");
            int protoIndex=this.input.indexOf("//");
            if(protoIndex<1)throw new RuntimeException("no protocal::");
           userInfo=  aStrings[0].split("//")[1];
           int syegeoStart=input.indexOf("//");
           int hostEnd=input.indexOf(":", syegeoStart+1);
           String hostportString=this.input.split("@")[1];
           host=hostportString.split(":")[0];
           port=Integer.parseInt(hostportString.split(":")[1]);
        		   //input.substring(syegeoStart+2,hostEnd);
           System.out.println("");
        }



