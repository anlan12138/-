系统代码


数据库连接部分
package cha1;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class DButils {
private static String driver;
private static String url;
private static String username;
private static String password;
static {
	driver="com.mysql.jdbc.Driver";
	url="jdbc:mysql://localhost:3306/sgms?characterEncoding=utf8&useSSL=true";
	username="root";
	password="grys007";
}
public static Connection open(){
	try {
		Class.forName(driver);
	} catch (ClassNotFoundException e) {
		
		e.printStackTrace();
	}
	try {
		return DriverManager.getConnection(url, username, password);
	} catch (SQLException e) {
		
		e.printStackTrace();
	}
	return null;
}
public static void close(Connection conn){
	if(conn!=null){
		try {
			conn.close();
		} catch (SQLException e) {
			e.printStackTrace();
		}
	}
}
 }


package cha1;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;


public class Test {

	public static void main(String[] args) {
		
		Connection conn=DButils.open();
		System.out.println("取得连接！");

		/*String sql2="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('24','2','82','1','一');";
		String sql4="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('24','3','84','1','一');";
		String sql6="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('24','4','88','1','一');";
		String sql1="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('25','1','88','1','一');";
		String sql2="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('25','2','86','1','一');";
		String sql3="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('25','3','84','1','一');";
		String sql1="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('26','1','90','1','一');";
		String sql2="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('26','2','90','1','一');";
		String sql3="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('26','3','99','1','一');";
		String sql4="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('26','4','88','1','一');";*/
		//String sql1="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('09','1','86','1','一');";
		//String sql2="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('09','2','85','1','一');";
		String sql3="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('25','3','88','1','一');";
		//String sql4="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values('09','4','87','1','一');";
		try {Statement stmt=conn.createStatement();
			//stmt.executeUpdate(sql1);
			//stmt.executeUpdate(sql2);
			stmt.executeUpdate(sql3);
		//	stmt.executeUpdate(sql4);
		} catch (SQLException e) {
			e.printStackTrace();
	}
}
	}






界面部分


package cha1;
import java.awt.*;
import java.awt.event.*;
import java.io.FileWriter;
import java.io.IOException;

public class InforFrame extends Frame implements ActionListener {
Label label1;
TextField textFiled1;
Label label2;
TextField textFiled2;
Button button1;
Button button2;
public InforFrame(){
	super("登录");
	setBackground(Color.pink);
	textFiled1=new TextField(10);//创建一个指定列数的文本框
	label1=new Label("您的学号：");//标签1
	label2=new Label();
	Panel p1=new Panel();
	p1.add(label1);
	p1.add(textFiled1);
	textFiled2=new TextField(10);
label2.setText("您的密码：");
    Panel p2=new Panel();
    p2.add(label2);//面板的布局管理默认Flowlayout（像水流装入容器）
    p2.add(textFiled2);
 	button1=new Button();
	button2=new Button();//创建按钮对象
	button1.setLabel("学生登录");
	button2.setLabel("教师登录");
	Panel p3=new Panel();
	p3.add(button1);
	p3.add(button2);
	add("North",p1);
	add("Center",p2);
	add("South",p3);
	setSize(280,220);
	setVisible(true);
	button1.addActionListener(this);
	button2.addActionListener(this);
}
public void actionPerformed(ActionEvent event){
	String command=event.getActionCommand();
	if(command.equals("学生登录")){
		if(textFiled2.getText().equals("0")&&textFiled1.getText()!=null){
			Frame3 frm3=new Frame3();
			dispose();			 }
		else	{textFiled2.setText(" ");}
	}
	else{
		if(command.equals("教师登录"));{
		if(textFiled2.getText().equals("1")&&textFiled1.getText()!=null)
		{Frame2 frm2=new Frame2();
		dispose();	}
		else	{textFiled2.setText(" ");}
		}
	}
	}
public static void main(String args[]){
	InforFrame frm=new InforFrame();
	 frm.addWindowListener(new java.awt.event.WindowAdapter()
	  { public void windowClosing(java.awt.event.WindowEvent e)
	             {
	                 System.exit(0);
	             }
	       });
	        
}
}


package cha1;
import java.awt.*;
import java.awt.event.*;
import java.io.FileWriter;
import java.io.IOException;


public class Frame2 extends Frame implements ActionListener {
	
	 
	 Button button2;
	 Button button3;
	 Button button4;
public  Frame2(){
	super("教师界面");
	setBackground(Color.pink);
	 Panel p1=new Panel();
	
	button2=new Button();
	button3=new Button();
	button4=new Button();
	
	button2.setLabel("删除记录");
	button3.setLabel("增加记录");
	button4.setLabel("更新记录");
	
	p1.add(button2);
	p1.add(button3);
	p1.add(button4);
	add("Center",p1);
	setSize(280,220);
	setVisible(true);
		button2.addActionListener(this);
		button3.addActionListener(this);
		button4.addActionListener(this);
		}
public void actionPerformed(ActionEvent event){
	String command=event.getActionCommand();
	if(command.equals("删除记录")){
		Frame4 frm4=new Frame4();
		dispose();	}
	else if(command.equals("增加记录")){
		Frame5 frm5=new Frame5();
		dispose();	
	}
	else if(command.equals("更新记录")){
		Frame6 frm6=new Frame6();
		dispose();	
	} }
}





package cha1;

import java.awt.*;
import java.awt.event.*;
import java.io.FileWriter;
import java.io.IOException;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class Frame3 extends Frame implements ActionListener{
	Label label1;
	Label label2;	
	Label label3;
	Button button4;
	Button button5;
	TextField textFiled1;
	TextField textFiled2;
	TextField textFiled3;
public Frame3(){
	super("查看成绩");
	setBackground(Color.pink);
	textFiled1=new TextField(10);
	textFiled2=new TextField(10);
	textFiled3=new TextField(20);
	label1=new Label("请填写学号");
	label2=new Label("请填写课程号");
	label3=new Label("你查询的成绩：");
	Panel p1=new Panel();
	Panel p3=new Panel();
	button4=new Button();
	button5=new Button();
	button4.setLabel("确认");
	button5.setLabel("返回");
	p1.add(label1);
	p1.add(textFiled1);
	p1.add(label2);
	p1.add(textFiled2);
	p1.add(label3);
	p1.add(textFiled3);
	p3.add(button4);
	p3.add(button5);
	add("South",p3);
	add("Center",p1);
	setSize(220,220);
	setVisible(true);
	button4.addActionListener(this);
	button5.addActionListener(this);
	}
public void actionPerformed(ActionEvent event){
	String command=event.getActionCommand();
		if(command.equals("确认")){
			Connection conn=DButils.open();
			String sql="select 成绩 from 学生分学期成绩表 where 学号=? and 课程号=?;";
			
				try {
					PreparedStatement pstmt =conn.prepareStatement(sql);
					pstmt.setString(1,textFiled1.getText());
					pstmt.setString(2,textFiled2.getText());
					ResultSet rs=pstmt.executeQuery();
					while(rs.next()){
						String a=rs.getString("成绩");
					textFiled3.setText("您查看的成绩为："+a);}

				} catch (SQLException e) {
					e.printStackTrace();
				}
		}				
		
		else if (command.equals("返回")){
			
			InforFrame frm=new InforFrame();
			dispose();	
			 frm.addWindowListener(new java.awt.event.WindowAdapter()
			  { public void windowClosing(java.awt.event.WindowEvent e)
			             {
			                 System.exit(0);
			             }
			       });
		}}
}



package cha1;
import java.awt.*;

import java.awt.event.*;
import java.io.FileWriter;
import java.io.IOException;
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
public class  Frame4 extends Frame implements ActionListener {
	Label label1;
	Button button1;
	Button button2;
	Button button3;
	Button button4;
	Button button5;
public Frame4(){
	super("删除记录");
	setBackground(Color.pink);
	label1=new Label("您删除的记录是：");
	Panel p1=new Panel();
	p1.add(label1);

	button1=new Button();
	button2=new Button();//创建按钮对象
	button3=new Button();
	button4=new Button();
	button5=new Button();
	button1.setLabel("九号");
	button2.setLabel("二十五号");
	button3.setLabel("二十六号");
	button4.setLabel("二十四号");
	button5.setLabel("返回");
	Panel p3=new Panel();
	p3.add(button1);
	p3.add(button2);
	p3.add(button3);
	p3.add(button4);
	p3.add(button5);
	add("Center",p1);
	add("South",p3);
	setSize(280,220);
	setVisible(true);
	button1.addActionListener(this);
	button2.addActionListener(this);
	button3.addActionListener(this);
	button4.addActionListener(this);
	button5.addActionListener(this);
}

public void actionPerformed(ActionEvent event){
	String command=event.getActionCommand();
	if(command.equals("九号")){
		Connection conn=DButils.open();
		
		String sql="delete from 学生分学期成绩表  where 学号=09;";
	try {Statement stmt;
		stmt = conn.createStatement();
			stmt.executeUpdate(sql);
		} catch (SQLException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}
		try {
			conn.close();
		} catch (SQLException e) {
			e.printStackTrace();
		}
	}
	else if(command.equals("二十五号")){
     Connection conn=DButils.open();
		
		String sql="delete from 学生分学期成绩表  where 学号=25;";
	try {Statement stmt;
		stmt = conn.createStatement();
			stmt.executeUpdate(sql);
		} catch (SQLException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}
		try {
			conn.close();
		} catch (SQLException e) {
			e.printStackTrace();
		}
	}
	else if(command.equals("二十六号")){
		  Connection conn=DButils.open();
			
			String sql="delete from 学生分学期成绩表  where 学号=26;";
		try {Statement stmt;
			stmt = conn.createStatement();
				stmt.executeUpdate(sql);
			} catch (SQLException e1) {
				// TODO Auto-generated catch block
				e1.printStackTrace();
			}
			try {
				conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
	}
	else if(command.equals("二十四号")){
		  Connection conn=DButils.open();
			
			String sql="delete from 学生分学期成绩表  where 学号=24;";
		try {Statement stmt;
			stmt = conn.createStatement();
				stmt.executeUpdate(sql);
			} catch (SQLException e1) {
				// TODO Auto-generated catch block
				e1.printStackTrace();
			}
			DButils.close(conn);
	}
	else if(command.equals("返回")){
		dispose();
		InforFrame frm=new InforFrame();
		frm.addWindowListener(new java.awt.event.WindowAdapter()
		  { public void windowClosing(java.awt.event.WindowEvent e)
		             {
		                 System.exit(0);
		             }
		       });
	}
	
}
}






package cha1;

import java.awt.Button;
import java.awt.Color;
import java.awt.Frame;
import java.awt.Label;
import java.awt.Panel;
import java.awt.TextField;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.sql.Statement;

public class Frame5  extends Frame implements ActionListener  {
	Label label1;
	Label label2;
	Label label3;
	Label label4;
	Label label5;
	Button button1;
	Button button2;
	TextField textFiled1;
	TextField textFiled2;
	TextField textFiled3;
	TextField textFiled4;
	TextField textFiled5;
public Frame5(){
	super("增加记录");
	setBackground(Color.pink);
	label1=new Label("请输入您要添加的学号");
	label2=new Label("请输入您要添加的课程号");
	label3=new Label("请输入您要添加的成绩");
	label4=new Label("请输入您要添加的学期号");
	label5=new Label("请输入您要添加的班级");
	textFiled1=new TextField(10);
	textFiled2=new TextField(10);
	textFiled3=new TextField(10);
	textFiled4=new TextField(10);
	textFiled5=new TextField(10);
	Panel p1=new Panel();
	p1.add(label1);
	p1.add(textFiled1);
	p1.add(label2);
	p1.add(textFiled2);
	p1.add(label3);
	p1.add(textFiled3);
	p1.add(label4);
	p1.add(textFiled4);
	p1.add(label5);
	p1.add(textFiled5);
	button1=new Button();
	button2=new Button();//创建按钮对象
    button1.setLabel("确认");
	button2.setLabel("返回");
	Panel p3=new Panel();
	p3.add(button1);
	p3.add(button2);
    add("Center",p1);
	add("South",p3);
	setSize(400,220);
	setVisible(true);
	button1.addActionListener(this);
	button2.addActionListener(this);
}
public void actionPerformed(ActionEvent event){
	String command=event.getActionCommand();
	if(command.equals("确认")){
		Connection conn=DButils.open();
		String sql="insert into 学生分学期成绩表(学号,课程号,成绩,学期号,班级)values(?,?,?,?,?);";
		try {
			PreparedStatement pstmt =conn.prepareStatement(sql);
			pstmt.setString(1,textFiled1.getText());
			pstmt.setString(2,textFiled2.getText());
			pstmt.setString(3,textFiled3.getText());
			pstmt.setString(4,textFiled4.getText());
			pstmt.setString(5,textFiled5.getText());
			pstmt.executeUpdate();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		DButils.close(conn);
	}
	else if(command.equals("返回")){
		InforFrame frm=new InforFrame();
		dispose();
		frm.addWindowListener(new java.awt.event.WindowAdapter()
		  { public void windowClosing(java.awt.event.WindowEvent e)
		             {
		                 System.exit(0);
		             }
		       });
	}
	
}
}







package cha1;

import java.awt.Button;
import java.awt.Color;
import java.awt.Frame;
import java.awt.Label;
import java.awt.Panel;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.Connection;
import java.sql.SQLException;
import java.sql.Statement;

public class Frame6 extends Frame implements ActionListener {
	Label label1;
	Button button1;
	Button button2;
	Button button3;
	Button button4;
	Button button5;
	public Frame6(){
		super("更新记录");
		setBackground(Color.pink);
		label1=new Label("您更新的记录是：");
		Panel p1=new Panel();
		p1.add(label1);
		button1=new Button();
		button2=new Button();//创建按钮对象
		button3=new Button();
		button4=new Button();
		button5=new Button();
		button1.setLabel("九号");
		button2.setLabel("二十五号");
		button3.setLabel("二十六号");
		button4.setLabel("二十四号");
		button5.setLabel("返回");
		Panel p3=new Panel();
		p3.add(button1);
		p3.add(button2);
		p3.add(button3);
		p3.add(button4);
		p3.add(button5);
		add("Center",p1);
		add("South",p3);
		setSize(280,220);
		setVisible(true);
		button1.addActionListener(this);
		button2.addActionListener(this);
		button3.addActionListener(this);
		button4.addActionListener(this);
		button5.addActionListener(this);
	}
	public void actionPerformed(ActionEvent event){
		String command=event.getActionCommand();
		if(command.equals("九号")){
			Connection conn=DButils.open();
			String sql="update  学生分学期成绩表  set 成绩='0' where 学号='09';";
		try {Statement stmt;
			stmt = conn.createStatement();
				stmt.executeUpdate(sql);
			} catch (SQLException e1) {
				// TODO Auto-generated catch block
				e1.printStackTrace();
			}
			try {
				conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}	
		else if(command.equals("二十五号")){
			Connection conn=DButils.open();
			String sql="update  学生分学期成绩表  set 成绩='0' where 学号='25';";
		try {Statement stmt;
			stmt = conn.createStatement();
				stmt.executeUpdate(sql);
			} catch (SQLException e1) {
				// TODO Auto-generated catch block
				e1.printStackTrace();
			}
			try {
				conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
		else if(command.equals("二十六号")){
			Connection conn=DButils.open();
			String sql="update  学生分学期成绩表  set 成绩='0' where 学号='26';";
		try {Statement stmt;
			stmt = conn.createStatement();
				stmt.executeUpdate(sql);
			} catch (SQLException e1) {
				// TODO Auto-generated catch block
				e1.printStackTrace();
			}
			try {
				conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
		else if(command.equals("二十四号")){
			Connection conn=DButils.open();
			String sql="update  学生分学期成绩表  set 成绩='0' where 学号='24';";
		try {Statement stmt;
			stmt = conn.createStatement();
				stmt.executeUpdate(sql);
			} catch (SQLException e1) {
				// TODO Auto-generated catch block
				e1.printStackTrace();
			}
			try {
				conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
		
		else if(command.equals("返回")){
			dispose();
			InforFrame frm=new InforFrame();
			frm.addWindowListener(new java.awt.event.WindowAdapter()
			  { public void windowClosing(java.awt.event.WindowEvent e)
			             {
			                 System.exit(0);
			             }
			       });
		}
	}
}
