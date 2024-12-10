Spring boot下，集成任务调度中心（XXL-JOB）


一、使用背景
　　目前项目中，采用的是微服务框架，由于在微服务中，存在需要定时的任务。但如果定时任务维护在每个微服务下，当微服务部署多个实例的情况下，会出现定事任务多次执行的情况。并且在解决问题的基础上，希望能够实现动态修改任务的定时时间，可以通过页面对定时任务进行控制。
二、XXL-JOB简单介绍
　　首先，XXL-JOB是一个轻量级分布式任务调度平台，内容采用了Quartz定时框架实现，服务之间通信通过RPC的方式实现。
　　其次，在功能方面：
支持通过web页面对任务进行增删改查操作
支持动态修改任务状态、启动、停止等，即时生效。
支持多种阻塞处理策略，如串行、丢弃后续调度、覆盖之前调度
支持超时控制、失败重试、邮件报警等处理

Spring cfg 


xxl:
  job:
    ### 执行器通讯TOKEN [选填]：非空时启用；
    accessToken:
    admin:
      ### 调度中心部署跟地址 [选填]：如调度中心集群部署存在多个地址则用逗号分隔。
      ### 执行器将会使用该地址进行"执行器心跳注册"和"任务结果回调"；为空则关闭自动注册；
      addresses: http://192.168.0.3:18080/top-job-admin
    executor:
      ### 执行器AppName [选填]：执行器心跳注册分组依据；为空则关闭自动注册
      appname: top-job-executor-finance
      ### 执行器IP [选填]：默认为空表示自动获取IP，多网卡时可手动设置指定IP，
      ### 该IP不会绑定Host仅作为通讯实用；地址信息用于 "执行器注册" 和 "调度中心请求并触发任务"；
      ip:
      ### 执行器端口号 [选填]：小于等于0则自动获取；默认端口为9999，单机部署多个执行器时，注意要配置不同执行器端口；
      port: 15558
      ### 执行器运行日志文件存储磁盘路径 [选填] ：需要对该路径拥有读写权限；为空则使用默认路径；
      logpath: ../logs/top-job/jobhandler
      ### 执行器日志保存天数 [选填] ：值大于3时生效，启用执行器Log文件定期清理功能，否则不生效；
      logretentiondays: 1


@JobHandler(value = "SumPPlBalanceGroupbyPlatDateJob")

package com.platform.top.xiaoyu.run.service.finance.job;

import com.platform.top.xiaoyu.run.service.finance.service.ISafeService;
import com.platform.top.xiaoyu.run.service.finance.service.impl.BalanceServiceImpl;
import com.xxl.job.core.biz.model.ReturnT;
import com.xxl.job.core.handler.IJobHandler;
import com.xxl.job.core.handler.annotation.JobHandler;
import com.xxl.job.core.log.XxlJobLogger;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

import java.util.Date;

@JobHandler(value = "SumPPlBalanceGroupbyPlatDateJob")
@Component
public class SumPPlBalanceGroupbyPlatDateJob extends IJobHandler {

   @Autowired
   BalanceServiceImpl BalanceServiceImpl1;

   @Override
   public ReturnT<String> execute(String param) throws Exception {
      XxlJobLogger.log("当前参数:{}", param);
      XxlJobLogger.log("执行计算 SumPPlBalanceGroupbyPlatDateJob start");

      //计算利息
      // iSafeService.calcJob();
      //if(new Date().getHours()>23)
         BalanceServiceImpl1.sumPplSumBalanceDateGrupbyPlat();

      XxlJobLogger.log("执行计算  SumPPlBalanceGroupbyPlatDateJob  end");
      return SUCCESS;
   }
}


管理 预调度器
增加192.168.0.177:15558
Appname with yml cg
top-job-executor-finance


建立任务，by调度器
SumPPlBalanceGroupbyPlatDateJob

执行ok

