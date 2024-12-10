Atitit tk.mybatis use


package application.dao;

import tk.mybatis.mapper.common.Mapper;
import application.model.ActivityHongbaoItem;
import application.model.SscBets;
import application.model.User;

public interface MySscBetsMapper  extends Mapper<User> {
}



	@Autowired
	MySscBetsMapper  mapper;// cant use tk.mybatis.mapper.common.Mapper direct
	
//	@Autowired
//	AtiSerive AtiSerive1;
	
	@Test
	public void testRedis() {
	
	CacheHelper.setCpapiParam("companyShortName",new HashMap<String, String>());
	}

	@Test
	public void test() {
	//	org.springframework.core.task.SyncTaskExecutor
	//	org.springframework.core.task.TaskExecutor
		///   
		// FileSystemXmlApplicationContext
	//	ApplicationContext ac = new ClassPathXmlApplicationContext("applicationContext.xml");
	//	HKLhcScheduleTest HKLhcSchedule1 = ac.getBean(HKLhcScheduleTest.class);
	//	HKLhcSchedule1.synLhc();
		
		
		 Example example = new Example(User.class);
	        Example.Criteria criteria = example.createCriteria();
 
//FROM sSC_bETS limit ?,? 
	        RowBounds rowBounds = new RowBounds(0, 1);
	        //com.github.pagehelper.Page import list itfs
	        List  sscOpenTimeList = mapper.selectByExampleAndRowBounds(example, rowBounds);
	     System.out.println(sscOpenTimeList.getClass());   
	      System.out.println(sscOpenTimeList);
	   //   AtiSerive1.upuser();
	      User u=new User();
	      u.setFreezingAmount(new BigDecimal(15));
	      u.setId(1688923L);
	      mapper.updateByPrimaryKeySelective( u);
	 System.out.println("--");
	      
	}

