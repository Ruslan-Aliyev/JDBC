# JDBC

```java
import java.sql.*;

public class JdbcDemonstration {
	public static void main(String[] args) {
	
		Connection con = null;
		Statement stmt = null;
		String sDriver = "com.mysql.jdbc.Driver";
		String sURL = "jdbc:mysql://_____";	//DATABASE LOCATION & DATABASE NAME
		String sUsername = "___"; //Username
		String sPassword = "___"; //Password
		
		try { // Attempt to load the JDBC driver with newInstance
			Class.forName(sDriver).newInstance();
		}catch( Exception e ) {
			System.err.println("Failed to load current driver. ");
			return;
		} // end catch
		
		try { //Connect to database
			con = DriverManager.getConnection (sURL, sUsername, sPassword);
			stmt = con.createStatement();
		}catch ( Exception e) {
			System.err.println("Problems connecting to " + sURL + ":" );
			System.err.println( e.getMessage() );
			if( con != null) {
				try { con.close(); }
				catch( Exception e2 ) {}
			}
			return;
		} // end catch			

		try { //Execute SQL queries
			stmt.executeUpdate(" ___ "); 
			//Put SQL queries inside double quotation marks 
			//EG: SELECT ___ FROM DatabaseName.TableName  WHERE ___=___
			
		}catch ( Exception e) {
			System.err.println( "Couldn't perform ...":" );
			System.err.println( e.getMessage() );
			return;
		} 		
		
		// Disconnect
		try { stmt.close(); }catch( Exception e ) {}
		try { con.close(); }catch( Exception e ) {}			
	}
}			
```
