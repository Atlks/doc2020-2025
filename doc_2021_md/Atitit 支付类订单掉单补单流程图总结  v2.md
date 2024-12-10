Atitit 支付类订单掉单补单流程图总结

补单流程流程图



补单流程伪代码
// 开元订单查询 orderQuery 3：暂时查询不到
	private void 开元补单流程(User user, ErrorOrder errorOrder, int orderQueryStat) {

		 if(远程订单存在状态) {
			     
			 远程订单不存在();
				if (上分订单) {
					// 用户余额回归
					// 更新补单日志
					// 刷新缓存
					// 删除本地补单记录
					return;
				}
				//
				else if (下分订单) {
					// 下分删除本地补单记录
					return;
				}
				return;
		 }
		 远程订单存在();
		 
		if (远程订单在处理中状态) {
			处理中();
			return;
		}
		远程订单处理完毕();
		

		// 远程订单处理完毕
		if (先检查本地订单是否存在) {
			//本地订单不存在
			return;
		}
		 本地掉单存在();
		if (查询远程订单状态) {
			远程订单状态成功();
			if (下分订单) {
				添加余额();
				// 更新补单日志
				// 删除本地补单记录
				// 刷新缓存
				return;

			} else if (上分订单) {
				// 更新本地订单为完成
				// 删除本地补单记录
				return;
			}
			return;
		}

		
		 
		 其他状态不做任何处理();
		// else if if (orderQueryStat != 0) not succuss and not processing state...
		// 订单不是成功状态，也不在处理中则直接删除本地记录
		// 默认为下分补单记录
		// 上分订单处理，上分订单失败，则需要将用户的钱回滚处理
		// 上分订单 thired is fail..,and loc already rds bal,,so local need return addmoney
		// 下分订单 thired is fail.and loca fail...and dont need do anything..
	
	}











