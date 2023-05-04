This Feature Deals with Automatic mailing based on student details of attended student.

Needs :  
>
        To send an email for Automatic Monitoring System:                                                               
          Step1 - Need to know wheather Student is Login or Logout based on founded data inside the login.txt file.     
          Step2 - Get the current date and time                                                                         
          Step3 - Define email sender and receiver                                                                      
          Step4 - Set the subject and body of the email                                                                 
          Step5 - Add SSL (layer of security)                                                                           
          Step6 - Log in and send the email                                                                             

Step1 - Need to know wheather Student is Login or Logout based on founded data inside the login.txt file.     <br>

    def update_login(student_name):
      file_path = '/content/drive/MyDrive/Colab Notebooks/Real_time_face_recognition_based_Attendance_monitoring_system/Attendance folder/login.txt'
      # student_name = input("Enter student name: ")

      with open(file_path, 'r') as file:
          lines = file.readlines()
      # print("initial>",lines)

      found = 0
      new_lines = []

      for line in lines:
          if line.strip() == student_name:
              found = 1 
              print(found,"<<")
              continue
          else:
              new_lines.append(line)

      if not found:
          new_lines.append(student_name + '\n')

      with open(file_path, 'w') as file:
          file.writelines(new_lines)

      with open(file_path, 'r') as file:
          lines = file.readlines()
      return found
      # print("final>",lines)
    ##################################
    founded = update_login(name) 
    
    
Step2 - Get the current date and time                                                                         <br>

    from datetime import datetime
    now = datetime.now(timezone("Asia/Kolkata"))
    current_time = now.strftime("%H:%M:%S")
    current_date = now.strftime("%d/%m/%Y")
    
Step3 - Define email sender and receiver                                                                      <br>

    email_sender = 'srisri.jakka@gmail.com'
    email_password = 'lxprtekjbjixaram'
    email_receiver = 'bnagaseshu2001@gmail.com'
    
Step4 - Set the subject and body of the email                                                                 <br>

    subject = 'SSNV Organisation REAL-TIME FACE RECOGNITION BASED ATTENDANCE MONITORING SYSTEM.'#'Check out Your ward attendance!'
    body = f"""
    <<<<<<<<<<<<<   YOUR ATTENDANCE   >>>>>>>>>>>>>>>
    -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    RollNo : {d[name][1]}                                                                        
    NAME : {name}                                                                                
    DATE : {current_date}                                                                         
    TIME : {current_time}    
    {name} {res_loginRout} attended on {current_date} at {current_time} has successfully marked the attendance.  
    ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    Dear {d[name][0]}, \n
    This message is from Organisation/college automatic attendance system. \n 
    Your attendance has been successfully marked using the face recognition system. This means that you have been present and accounted for during work hours. I would like to take this opportunity to congratulate you on your successful use of the system.
    \n
    The face recognition system has also enhanced our security measures, as it only allows authorized personnel with registered faces to enter the premises. This ensures that our workplace remains safe and secure at all times.
    \n
    As a Organisation/college attendance system would like to remind you to continue using the face recognition system for attendance marking. It is important that we maintain accurate attendance records to ensure that everyone is accounted for during work hours..
    \n
    Thank you for your attention to this matter.
    \n
    Best regards,
    \n
    {name}"""

    em = EmailMessage()
    em['From'] = 'XYZ'#email_sender
    em['To'] = email_receiver
    em['Subject'] = subject
    em.set_content(body)
    
Step5 - Add SSL (layer of security)                                                                           <br>

    context = ssl.create_default_context()
    
Step6 - Log in and send the email                                                                             <br>

    with smtplib.SMTP_SSL('smtp.gmail.com', 465, context=context) as smtp:
      smtp.login(email_sender, email_password)
      smtp.sendmail(email_sender, email_receiver, em.as_string()) 
    print(f"emailsent to {name}")
    
    
   
OVERALL FINAL CODE IS:

    #--------CODE FOR EMAIL SENDING ----------------------
    import smtplib
    import ssl
    from email.message import EmailMessage
    from datetime import datetime
    import collections
    from pytz import timezone
    resulted_founded_names = ['SRISRI']
    d = collections.defaultdict(lambda : 'Not found')#['vilasagaram.vikas@gmail.com','20R25A0421'] )
    d ['SRISRI'] = ['srisri.jakka@gmail.com','19R21A04K7'] ;       d['NAGASESHU'] = ['bnagaseshu2001@gmail.com' ,'19R21A04K2'] 
    d ['VIKAS']  = ['vilasagaram.vikas@gmail.com','20R25A0421'] ;  d['VAMSI']  = ['vamsi251002@gmail.com', '20R25A0420']
    d ['VIKAS1']  = ['vilasagaram.vikas@gmail.com','20R25A0421'] ; d ['VIKAS2']  = ['vilasagaram.vikas@gmail.com','20R25A0421']
    for name in resulted_founded_names:
      try:
        if d[name] == 'Not found': pass

      ##################################
        def update_login(student_name):
          file_path = '/content/drive/MyDrive/Colab Notebooks/Real_time_face_recognition_based_Attendance_monitoring_system/Attendance folder/login.txt'
          # student_name = input("Enter student name: ")

          with open(file_path, 'r') as file:
              lines = file.readlines()
          # print("initial>",lines)

          found = 0
          new_lines = []

          for line in lines:
              if line.strip() == student_name:
                  found = 1 
                  print(found,"<<")
                  continue
              else:
                  new_lines.append(line)

          if not found:
              new_lines.append(student_name + '\n')

          with open(file_path, 'w') as file:
              file.writelines(new_lines)

          with open(file_path, 'r') as file:
              lines = file.readlines()
          return found
          # print("final>",lines)
        ##################################
        founded = update_login(name)
        res_loginRout = "Login time"
        if founded: res_loginRout = "Logout time"
        print(founded,res_loginRout)
        for i in range(1):
          # Get the current date and time
          now = datetime.now(timezone("Asia/Kolkata"))
          current_time = now.strftime("%H:%M:%S")
          current_date = now.strftime("%d/%m/%Y")

          # for i in range(10):
          # Define email sender and receiver
          email_sender = 'srisri.jakka@gmail.com'
          email_password = 'lxprtekjbjixbsri'
          email_receiver = d[name][0]#'skgouse131@gmail'#'bnagaseshu2001@gmail.com'#'vilasagaram.vikas@gmail.com'#'skgouse131@gmail.com'

          # Set the subject and body of the email
          subject = 'SSNV Organisation REAL-TIME FACE RECOGNITION BASED ATTENDANCE MONITORING SYSTEM.'#'Check out Your ward attendance!'
          body = f"""
          <<<<<<<<<<<<<   YOUR ATTENDANCE   >>>>>>>>>>>>>>>
          -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
          RollNo : {d[name][1]}                                                                        
          NAME : {name}                                                                                
          DATE : {current_date}                                                                         
          TIME : {current_time}    
          {name} {res_loginRout} attended on {current_date} at {current_time} has successfully marked the attendance.  
          ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
          Dear {d[name][0]}, \n
          This message is from Organisation/college automatic attendance system. \n 
          Your attendance has been successfully marked using the face recognition system. This means that you have been present and accounted for during work hours. I would like to take this opportunity to congratulate you on your successful use of the system.
          \n
          The face recognition system has also enhanced our security measures, as it only allows authorized personnel with registered faces to enter the premises. This ensures that our workplace remains safe and secure at all times.
          \n
          As a Organisation/college attendance system would like to remind you to continue using the face recognition system for attendance marking. It is important that we maintain accurate attendance records to ensure that everyone is accounted for during work hours..
          \n
          Thank you for your attention to this matter.
          \n
          Best regards,
          \n
          {name}"""

          em = EmailMessage()
          em['From'] = 'XYZ'#email_sender
          em['To'] = email_receiver
          em['Subject'] = subject
          em.set_content(body)

          # Add SSL (layer of security)
          context = ssl.create_default_context()

          # Log in and send the email
          with smtplib.SMTP_SSL('smtp.gmail.com', 465, context=context) as smtp:
              smtp.login(email_sender, email_password)
              smtp.sendmail(email_sender, email_receiver, em.as_string()) 
          print(f"emailsent to {name}") 
        resulted_founded_names = []
      except:
        print("NO match found")
    #------------------------------------------------------------------------
