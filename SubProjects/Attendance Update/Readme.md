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
