# Spring-BeanApplication
SpringBeanApplication 
package com.nt.service;
import com.nt.bo.*;
import com.nt.dao.*;
import com.nt.dto.*;
import com.nt.service.*;
public class StudentServiceImple implements StudentServices {
	private StudentDAO dao;
	public StudentDAOImplm(StudentDAOImplm dao) {
		this.dao=dao;
		
	}//end of the constructor 
	@Override
	public String generateResult(StudentDAO dto) {
		//write B.logic 
		int total=dto.getM1()+dto.getM2()+dto.getM3	();
		float avg=(float)total/3.0f;
		String result=null;
		if(avg<35) {
			result="fail";
			
		}else {
			result="pass";
		}
		//create bo object 
		StudentBO bo=new StudentBO();
		bo.setSno(total);
		bo.setSname(result);
		bo.setTotal(total);
		bo.setAvg(avg);
		bo.setResult(result);
		//use DAO
		int cnt=dao.insert(bo);
		if(cnt==0) {
			return "Result "+bo.getResult()+" "+bo.getSno()+"Registation Fail";
		}else {
			
			return "Result"+bo.getResult()+bo.getSno()+"Registation Succedded";
		}
		
	}//end of the method 
	
}//end of the class
