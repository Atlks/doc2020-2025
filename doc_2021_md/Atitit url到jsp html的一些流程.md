Atitit url到jsp html的一些流程


	@RequestMapping(value = "/budanList.html", method = RequestMethod.GET)
	public ModelAndView budanList(HttpServletRequest request) {
		Map<String, Object> modelMap = new HashMap<String, Object>();
//		AdminUser adminUser = SessionHelper.getAdminUserSession(httpServletRequest);
//		String com = adminUser.getCompanyShortName();
	 
	//	DailyRewardsTimeSettingDto timeSettingDto = webSettingService.getDailyTimeSetting(com);
//		request.setAttribute("obj", dto);
//		request.setAttribute("timeSetting", timeSettingDto);
		return this.renderView("systemSetting/budanList.html", modelMap);
	}

    /**
     * 渲染视图
     *
     * @param jspLocation
     * @param modelMap
     * @return ModelAndView
     */
    protected ModelAndView renderView(String jspLocation, Map<String, Object> modelMap) {
        ModelAndView modelAndView = new ModelAndView(jspLocation);
        AdminUser adminUser = SessionHelper.getAdminUserSession(httpServletRequest);
        modelMap.put("adminUserSession", adminUser);
        modelAndView.addAllObjects(modelMap);
        return modelAndView;
    }


/admin/src/main/resources/spring/spring-mvc.xml
    <!-- 对模型视图添加前后缀 -->
    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/view/"/>
        <property name="suffix" value=".jsp"/>
        
    </bean>
