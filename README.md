<project>

<property name="src" value="src"/>
<property name="classes" value="classes"/>

<target name="compile">
<javac srcdir="${src}" destdir="${classes}" includeantruntime="on"/>
</target>

<target name="run" depends="compile">
<java classname="helloworld" classpath="${classes}"/>
</target>

<target name="runn" depends="compile">
<java classname="TestRunner" classpath="${classes}"/>
</target>


</project>


import org.junit.runner.JUnitCore;
import org.junit.runner.Result;
import org.junit.runner.notification.Failure;

public class TestRunner {
	public static void main(String[] args) { 
		Result result = JUnitCore.runClasses(TestJunit.class);
		for(Failure failure : result.getFailures()) {
			System.out.println(failure.toString());
		}
		System.out.println(result.wasSuccessful());
	}
}


import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class TestJunit {
	String message = "Hello World";
	helloworld hw = new helloworld();
	@Test
	public void testPrint(){
		assertEquals(message, hw.get_text());
	}
}
