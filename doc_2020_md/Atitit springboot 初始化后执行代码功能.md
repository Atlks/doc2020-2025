Atitit springboot 初始化后执行代码功能


实现方法 ApplicationRunner .run()

@FunctionalInterface
public interface ApplicationRunner {
    void run(ApplicationArguments args) throws Exception;
}
获取变量内容。。



   @Value("${spring.profiles.active}")
   private String spring_profiles_active;
   public static void main(String[] args) {

      TopLaunchApplication.run(CommonConstant.APPLICATION_SERVICE_FS_BOOK_NAME, TopFsApplication.class, args);
   }

// @Autowired
// private IResourceFeginClient resourceFeginClient;

   /**
    * 上报授权服务资源
    */
   @Override
   public void run(ApplicationArguments args) {

      System.out.println("______________=================******************atti::"+spring_profiles_active );
   System.exit(0);
//    List<RpcCreateResourceReq> createResourceReqs = RegistServiceResourceUtil.scan("/top-service-finance", "com.platform.top.xiaoyu.run.service.finance.controller");
//     resourceFeginClient.updateServiceResources(createResourceReqs);
   }
}

