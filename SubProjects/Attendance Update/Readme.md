# ATTENDANCE DATABASE UPDATE
This Feature is to update the Attendance of the Attended Student Login and Logout in Attendance Folder on Login.txt and attendance.txt Files.                  <br>

<pre>
Need : To Update Attendance you are required to create a Folder                                                                                                <br>
Solution: I like to use google drive is my storage because to overcome the disasters Cloud storage is best solution.So i prefer Google Drive.                  <br>
         >Folder Creation: Open Google Drive                                                                                                                   <br>
         >Create a Folder: with Folder name as you like or i prefer "Attendance folder".Because this is the folder name we used for this project.              <br>
         >Create 2 text Files: 1.One File for attendance.txt     -> To store the Log data in the formate of "StudentName with Login/Logout and Date and Time". <br>
                               2.Another File for Login.txt      -> To store the List of Login or Presented Students.                                          <br>


</pre>
Need : To open the File in the Project                                                                                                                         <br>
>Solution: 
>>        with open(file_path, 'r') as file:
>>            lines = file.readlines()
>       Where, file_path='/content/drive/MyDrive/Colab Notebooks/Real_time_face_recognition_based_Attendance_monitoring_system/Attendance folder/login.txt' 
>       The above path is an example of input path file as login.txt
>       lines is a list of lines in the file.
>       ex:
>       _________________________
>       |Login.txt               | 
>       |------------------------|
>       |  Srisri                |
>       |  Seshu                 |
>       |________________________|     for this login.txt  >output> lines = [ 'Srisri\n' , 'Seshu\n' ] 
       
       
Need : To write in a file just opened aboe with new content of lines.
>Solution:                                                                                                                                                    
>>        with open(file_path, 'w') as file:
>>          file.writelines(new_lines)
>       Where, file_path='/content/drive/MyDrive/Colab Notebooks/Real_time_face_recognition_based_Attendance_monitoring_system/Attendance folder/login.txt' 
>       The above path is an example of input path file as login.txt
>       new_lines is a list of lines in the file.
>       ex:
>       new_lines = [ 'VamsiAnurag\n' , 'Srisri\n' , 'Seshu\n' , 'Vikas\n' ]
>       for this new_lines input login.txt becomes >
>       _________________________
>       |Login.txt               | 
>       |------------------------|
>       |  VamsiAnurag           |
>       |  Srisri                |
>       |  Seshu                 |
>       |  Vikas                 |
>       |________________________| 


Need : I want List of students in the class as a file as login.txt.
>Solution:
>
>                  Algorithm:
>                  1.I want to find wheather student is login or not?
>                  2.If student is already found logged then now the student is attended for logout.In this case i like to remove the name of student in the login.txt
>                  3.If student is not found in login.txt then this is the time of student login so i like to add the student name in the login.txt
>


<pre>
def update_login(student_name):
      # This is My login.txt File path 
      file_path = '/content/drive/MyDrive/Colab Notebooks/Real_time_face_recognition_based_Attendance_monitoring_system/Attendance folder/login.txt'
      # student_name = input("Enter student name: ")

      # I would like to open and read the lines of login.txt file
      with open(file_path, 'r') as file:
          lines = file.readlines()
      print("initial>",lines)

      #let till now student is not found i like to serch inside the login.txt
      found = 0
      new_lines = []

      for line in lines:
          #if student scaned by Attendance system is Already Login then 
          #i need to remove it in new file so remove adding student name in new_lines
          if line.strip() == student_name:
              found = 1 
              print(found,"<<")
              continue
          else:
              new_lines.append(line)  

      #If the student is not found in the login list then i need to add the student name in the login.txt by new_lines
      if not found:
          new_lines.append(student_name + '\n')

      #Write the new_lines in the login.txt to modify the changes
      with open(file_path, 'w') as file:
          file.writelines(new_lines)

      #to verify the resulted login.txt file open in readmode and Print the output.
      with open(file_path, 'r') as file:
          lines = file.readlines()
      print("final>",lines)
      for i in lines:
        print(i)
      return found

# I need to provide the input of Student name to update_login function to modify the login.txt
update_login("Spark")
</pre>

## RESULTS:
>   Login.txt Modification in case 1
>![LoginUpdate1](https://user-images.githubusercontent.com/106643865/236175776-24f05797-cc5e-408e-b9b9-2ac345c16cc3.png)
>   Login.txt Modification in case 2
>![LoginUpdate2](https://user-images.githubusercontent.com/106643865/236175801-7044db82-7764-4b26-acb5-78ab895e34e0.png)
