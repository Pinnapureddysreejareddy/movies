# movies

CREATE TABLE mymovie
(NAME VARCHAR(20) PRIMARY KEY,
ACTOR VARCHAR(15),
ACTRESS VARCHAR(15),
DIRECTOR VARCHAR(15),
YEAROFRELEASE INT(4)
);

INSERT INTO mymovie (NAME, ACTOR, ACTRESS, DIRECTOR, YEAROFRELEASE) VALUES ('Inception', 'Leo DiCaprio', 'Talulah Riley', 'C. Nolan', 2010);
INSERT INTO mymovie (NAME, ACTOR, ACTRESS, DIRECTOR, YEAROFRELEASE) VALUES ('The Dark Knight', 'Christian Bale', 'M. Gyllenhaal', 'C. Nolan', 2008);
INSERT INTO mymovie (NAME, ACTOR, ACTRESS, DIRECTOR, YEAROFRELEASE) VALUES ('Titanic', 'Leo DiCaprio', 'Kate Winslet', 'James Cameron', 1997);
INSERT INTO mymovie (NAME, ACTOR, ACTRESS, DIRECTOR, YEAROFRELEASE) VALUES ('Top Gun', 'Tom Cruise', 'Kelley McGillis', 'Jon Favreau', 1986);
INSERT INTO mymovie (NAME, ACTOR, ACTRESS, DIRECTOR, YEAROFRELEASE) VALUES ('Iron Man', 'Robert Downey', 'Gwyneth P', 'Jon Favreau', 2008);

SELECT * FROM mymovie;
SELECT NAME, ACTOR, ACTRESS, DIRECTOR, YEAROFRELEASE FROM mymovie;

SELECT NAME, ACTOR, ACTRESS, DIRECTOR, YEAROFRELEASE FROM mymovie
Where ACTOR = "Christian Bale";

SELECT NAME, ACTOR, ACTRESS, DIRECTOR, YEAROFRELEASE FROM mymovie
Where ACTOR = "Leo DiCaprio"
ORDER BY YEAROFRELEASE;

// When connected to a JAVA Application
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
public static void main(String[] args) 
{
 try
{
Class.forName("java.sql.Driver");
Connection con=DriverManager.getConnection("jdbc:mysql://localhost/mymovies","root","student");
Statement stmt=con.createStatement();
String query="select name,actor,actress,director,yearofrelease from mymovie where actor="Christian Bale";

ResultSet rs=stmt.executeQuery(query);

if(rs.next())
{

String n1=rs.getString("Name");
String n2=rs.getString("Actor");
String n3=rs.getString("Actress");
String n4=rs.getString("Director");
String n5=rs.getString("Yearofrelease");

jTextField5.setText(""+n5);
jTextField8.setText(""+n1);
jTextField7.setText(""+n2);
jTextField6.setText(""+n3);
jTextField10.setText(""+n4);

}

rs.close();
con.close();
stmt.close();
}
             catch(Exception e)
            {
            JOptionPane.showMessageDialog(null,"Error");
            
            } 
}
