from tkinter import *
from tkinter import messagebox
import random
import pyodbc

def result():
    qui.destroy()
    global res
    res = Toplevel()
    res.state("zoom")
    res.title("Quizzical Suspects")

    # FRAMES:
    res_mainframe= Frame(res, bg="rosy brown", borderwidth=10, highlightthickness=2, relief=GROOVE)
    res_mainframe.place(height=710, width=1367)

    bg_img = PhotoImage(file=r'C:\Users\USER\Desktop\quiz\bg.png')
    bg_img_s = bg_img.subsample(1, 1)
    bg_img_l = Label(res_mainframe, image=bg_img_s)
    bg_img_l.pack()

    result_frame = Frame(res_mainframe, bg="white", borderwidth=10, highlightthickness=0)
    result_frame.place(x=45, y=40, width=1250, height=610)

    success_img = PhotoImage(file=r'C:\Users\USER\Desktop\quiz\success_image.png')
    success_img_s = success_img.subsample(1, 1)
    success_img_l = Label(res_mainframe, image=success_img_s, borderwidth=0)
    success_img_l.image = success_img_s
    success_img_l.place(relx=0.61, rely=0.27)

    # LABELS:
    result_label = Label(result_frame, bg="white", text="RESULT", fg="black",
                         font=("BookmanOldStyle 32 bold underline"))
    result_label.place(relx=0.42, rely=0.08)

    score_label = Label(result_frame, text="SCORE OBTAINED:", font=("Yu Gothic UI Semibold",17), bg="white",
                        fg="black", width=20)
    score_label.place(relx=0.28, rely=0.4)

    total_label = Label(result_frame, text="TOTAL SCORE:", font=("Yu Gothic UI Semibold",17), bg="white", fg="black",
                        width=20)
    total_label.place(relx=0.26, rely=0.5)

    status_label = Label(result_frame, text="STATUS:", font=("Yu Gothic UI Semibold",17), bg="white", fg="black",
                         width=20)
    status_label.place(relx=0.24, rely=0.6)

    # Score:
    score_obtained = score

    score_show = Label(result_frame, text=score_obtained, font=("Stencil", 20), bg="white", fg="black", width=5)
    score_show.place(relx=0.48, rely=0.4)

    total_show = Label(result_frame, text="5", font=("Stencil", 20), bg="white", fg="black", width=5)
    total_show.place(relx=0.48, rely=0.5)

    # Status:
    if score_obtained <= 2:
        status="Fail"
        status_show = Label(result_frame, text="FAIL", font=("Stencil",20), bg="white", fg="red", width=10)
        status_show.place(relx=0.45, rely=0.6)

        status_label = Label(result_frame, text="BETTER LUCK NEXT TIME", font=("Lucida", 18, "bold"), bg="white",
                             fg="violet red")
        status_label.place(relx=0.36, rely=0.25)

    else:
        status="Pass"
        status_show = Label(result_frame, text="PASS", font=("Stencil",20), bg="white", fg="deep pink", width=10)
        status_show.place(relx=0.45, rely=0.6)

        status_label = Label(result_frame, text="YOU HAVE DONE GREAT", font=("Lucida", 18, "bold"), bg="white",
                             fg="midnight blue")
        status_label.place(relx=0.37, rely=0.25)


    # insert marks into database:
    Username = ename.get()

    con = pyodbc.connect(r'DRIVER={Microsoft Access Driver (*.mdb, *.accdb)};'
                         r'DBQ=C:\Users\USER\Desktop\quiz\Quiz.accdb;')
    insert = con.cursor()
    insert.execute(
        f"INSERT INTO Record(Username,Total_Score,Score_Obtained,Status)values('{Username}','{5}','{score_obtained}','{status}')")
    con.commit()
    con.close()

    # Button Commands:
    def homepage():
        res.destroy()
        records()

    def tryagain():
        res.destroy()
        quiz_home()

    # Button hover effect:
    def on_enter(e):
        e.widget['background'] = 'purple'
    def on_leave(e):
        e.widget['background'] = 'grey'

    # BUTTONS:

    btn_label = Label(result_frame, bg="Plum")
    btn_label.pack(fill=X, ipady=12, side=BOTTOM)

    home_btn = Button(btn_label, text="HomePage", bg="grey", fg="white", width=15, height=1,
                      font=("Fira Code", 15), command=homepage)
    home_btn.place(relx=0.25)
    home_btn.bind("<Enter>", on_enter)
    home_btn.bind("<Leave>", on_leave)

    tryagain_btn = Button(btn_label, text="Try Again", bg="grey", fg="white", width=15,
                          height=1, font=("Fira Code", 15), command=tryagain)
    tryagain_btn.place(relx=0.62)
    tryagain_btn.bind("<Enter>", on_enter)
    tryagain_btn.bind("<Leave>", on_leave)


    res.mainloop()


def quiz():
    hom.destroy()
    global qui
    qui = Toplevel()
    qui.state("zoom")
    qui.title("Quizzical Suspects")

   # FRAMES:
    quiz_mainframe = Frame(qui, bg="rosy brown", borderwidth=10, highlightthickness=2, relief=GROOVE)
    quiz_mainframe.place(height=710, width=1367)

    img1 = PhotoImage(file=r'C:\Users\USER\Desktop\quiz\bg.png')
    img2 = img1.subsample(1, 1)
    l1 = Label(quiz_mainframe, image=img2)
    l1.pack()

    quiz_frame = Frame(quiz_mainframe, bg="white", borderwidth=10, highlightthickness=0)
    quiz_frame.place(x=45, y=590, width=1250, height=70)

    # Button Commands:

    def submit():
        result()

    # globalising score:
    global score
    score = 0

    # Display Next Que:
    def next_que():
        global count
        if(count < 5):
          getting_ques_from_db(quiz_mainframe)
        else:
            qui.destroy()
            result()

        count = count + 1

    # Button hover effect:

    def on_enter(e):
            e.widget['background'] = 'purple'
    def on_leave(e):
            e.widget['background'] = 'grey'

    # BUTTONS:

    btn_label = Label(quiz_frame, bg="Plum")
    btn_label.pack(fill=X, ipady=12, side=BOTTOM)

    submit_btn = Button(btn_label, text="Submit", bg="grey", fg="white", width=15, height=1, font=("Fira Code", 15),
                                    command=submit)
    submit_btn.place(relx=0.15, rely=0.0)
    submit_btn.bind("<Enter>", on_enter)
    submit_btn.bind("<Leave>", on_leave)

    next_btn = Button(btn_label, text="Next", bg="grey", fg="white", width=15, height=1, font=("Fira Code", 15),
                                  command=next_que)
    next_btn.place(relx=0.7, rely=0.0)
    next_btn.bind("<Enter>", on_enter)
    next_btn.bind("<Leave>", on_leave)

    getting_ques_from_db(quiz_mainframe)

    qui.mainloop()

# Displaying Questions:
def getting_ques_from_db(quiz_mainframe):
    con = pyodbc.connect(r'DRIVER={Microsoft Access Driver (*.mdb, *.accdb)};'
                         r'DBQ=C:\Users\USER\Desktop\quiz\Quiz.accdb;')
    cur = con.cursor()
    cur.execute("Select * from Mcqs where Level='" + quiz_level + "' and Subject='" + sub + "' and status = 'N'")
    data = cur.fetchall()

    random_ques = random.sample(data, 1)
    print(random_ques)

    ans = IntVar()

    for i in random_ques:
        que_frame = Frame(quiz_mainframe, bg="White", borderwidth=10, highlightthickness=0)
        que_frame.place(x=45, y=40, width=1250, height=560)

        queman_img = PhotoImage(file=r'C:\Users\USER\Desktop\quiz\question_man.png')
        queman_img_s = queman_img.subsample(2, 2)
        queman_img_l = Label(que_frame, image=queman_img_s, borderwidth=0)
        queman_img_l.image=queman_img_s
        queman_img_l.place(rely=0.3)

        # LABELS:
        quiz_label = Label(que_frame, text="Quizical Suspects",
                           font=("BookmanOldStyle 32 bold underline"), bg="White", fg="Black")
        quiz_label.place(relx=0.32, rely=0.02)

        knowledge_label = Label(que_frame, text="Game Of Knowledge", font=("BookmanOldStyle 15 bold"),
                                bg="White", fg="Pink")
        knowledge_label.place(relx=0.39, rely=0.12)

        queno_label = Label(que_frame, text="Que-", bg="White", fg="Black", font=("TimesNewRoman", 18))
        queno_label.place(relx=0.2, rely=0.22)

        que_label = Label(que_frame, text=i[2], bg="White",fg="Black", font=("TimesNewRoman", 18))
        que_label.place(relx=0.25, rely=0.22)

        # Check Button Command:
        def getuseranswer():
            global score
            global answer
            answer = ans.get()
            if answer == i[7]:
              score +=1

        # CheckButtons:

        opta_btn = Checkbutton(que_frame, text=i[3],variable=ans,offvalue=0,onvalue=1,bg="White", height=1,font=("Fira Code", 18) , command=getuseranswer)
        opta_btn.place(relx=0.35, rely=0.4)

        optb_btn = Checkbutton(que_frame, text=i[4],variable=ans,offvalue=0,onvalue=2, bg="White", height=1,font=("Fira Code", 18) , command=getuseranswer)
        optb_btn.place(relx=0.35, rely=0.5)

        optc_btn = Checkbutton(que_frame, text=i[5],variable=ans,offvalue=0,onvalue=3, bg="White", height=1,font=("Fira Code", 18) , command=getuseranswer)
        optc_btn.place(relx=0.35, rely=0.6)

        optd_btn = Checkbutton(que_frame, text=i[6],variable=ans,offvalue=0,onvalue=4, bg="White", height=1,font=("Fira Code", 18) , command=getuseranswer)
        optd_btn.place(relx=0.35, rely=0.7)

        # Updating status to Y after getting the que from db:
        cur.execute("update Mcqs set status='Y' where Level='" + quiz_level + "' and Subject='" + sub + "' and Sno="+str(i[0])+"  and status = 'N'")

    con.commit()
    con.close()


def quiz_home():
    rec.destroy()
    global hom,count
    count = 1
    hom=Toplevel()
    hom.state("zoomed")
    hom.title("Quizzical Suspects")

    # FRAMES:
    hom_mainframe = Frame(hom, bg="rosy brown", borderwidth=10, highlightthickness=2, relief=GROOVE)
    hom_mainframe.place(height=710, width=1367)

    bg_img = PhotoImage(file=r'C:\Users\USER\Desktop\quiz\bg.png')
    bg_img_s = bg_img.subsample(1, 1)
    bg_img_l = Label(hom_mainframe, image=bg_img_s)
    bg_img_l.pack()

    home_frame1 = Frame(hom_mainframe, bg="White", borderwidth=10, highlightthickness=0)
    home_frame1.place(x=45, y=40, width=1250, height=610)
    home_frame2 = Frame(home_frame1, bg="burlywood1", borderwidth=10, highlightthickness=0)
    home_frame2.place(x=45, y=40, width=590, height=480)

    # LABELS:
    diff_label = Label(home_frame2, text="CHOOSE DIFFICULTY LEVEL", font=("BookmanOldStyle 18 bold"),
                       bg="burlywood1",fg="Purple")
    diff_label.place(relx=0.19, rely=0.11)

    sub_label = Label(home_frame2, text="CHOOSE SUBJECT", font=("BookmanOldStyle 18 bold"),
                       bg="burlywood1",fg="Purple")
    sub_label.place(relx=0.26, rely=0.59)

    read_label = Label(home_frame1, text="INSTRUCTIONS", font=("BookmanOldStyle 28 bold underline"), bg="White",
                       fg="Black")
    read_label.place(relx=0.65, rely=0.16)
    read_label2 = Label(home_frame1, text=("* This quiz contains 5 questions\n\n*Each question carries 1 mark\n\n"
                                           "* Once you move on to the next question\nyou cannot go back\n\n"
                                           "* On 5th question the next button\nwill submit your quiz\n"),
                        font=("Comis Sans MS", 16), bg="white")
    read_label2.place(relx=0.61, rely=0.32)

    # RADIOBUTTONS
    var1 = IntVar()
    easy_btn = Radiobutton(home_frame2, text="Easy", variable=var1, value=1, bg="burlywood1", width=10, height=1,
                           font=("Fira Code", 16))
    easy_btn.place(relx=0.3, rely=0.25)

    medium_btn = Radiobutton(home_frame2, text="Medium", variable=var1, value=2, bg="burlywood1", width=10, height=1,
                             font=("Fira Code", 16))
    medium_btn.place(relx=0.32, rely=0.35)

    hard_btn = Radiobutton(home_frame2, text="Hard", variable=var1, value=3, bg="burlywood1", width=10, height=1,
                           font=("Fira Code", 16))
    hard_btn.place(relx=0.3, rely=0.45)

    var2 = IntVar()
    PL_btn = Radiobutton(home_frame2, text="PL", variable=var2, value=1, bg="burlywood1", width=10, height=1,
                           font=("Fira Code",16))
    PL_btn.place(relx=0.3, rely=0.72)

    FIT_btn = Radiobutton(home_frame2, text="FIT", variable=var2, value=2, bg="burlywood1", width=10, height=1,
                             font=("Fira Code", 16))
    FIT_btn.place(relx=0.3, rely=0.82)


    # Button Commands:
    def home():
        hom.destroy()
        records()

    # Start Quiz:
    def start():
        con = pyodbc.connect(r'DRIVER={Microsoft Access Driver (*.mdb, *.accdb)};'
                             r'DBQ=C:\Users\USER\Desktop\quiz\Quiz.accdb;')
        cur = con.cursor()
        cur.execute("update Mcqs set status='N' where status = 'Y'")
        con.commit()
        con.close()

        value1 = var1.get()
        value2 = var2.get()
        global quiz_level
        global sub

        if value1 == 1 and value2==1:
            quiz_level="Easy"
            sub="PL"
            quiz()
        elif value1 == 2 and value2==1:
            quiz_level="Medium"
            sub="PL"
            quiz()
        elif value1 == 3 and value2==1:
            quiz_level="Hard"
            sub="PL"
            quiz()
        elif value1 == 1 and value2==2:
            quiz_level="Easy"
            sub="FIT"
            quiz()
        elif value1 == 2 and value2==2:
            quiz_level="Hard"
            sub="FIT"
            quiz()
        elif value1 == 3 and value2==2:
            quiz_level="Hard"
            sub="FIT"
            quiz()
        else:
            error_label=Label(home_frame1,text="SELECT LEVEL AND SUBJECT", font=("Microsoft YaHei UI", 15),fg="red",bg="White")
            error_label.place(relx=0.65, rely=0.85)

    # Button hover effect:

    def on_enter(e):
        e.widget['background'] = 'purple'
    def on_leave(e):
        e.widget['background'] = 'grey'

    # BUTTONS:

    btn_label = Label(home_frame1, bg="Plum")
    btn_label.pack(fill=X, ipady=12, side=BOTTOM)

    start_btn = Button(btn_label, text="Start Quiz", bg="Grey", fg="White", width=15, height=1, font=("Fira Code", 15),
                       command=start)
    start_btn.place(relx=0.7, rely=0.0)
    start_btn.bind("<Enter>", on_enter)
    start_btn.bind("<Leave>", on_leave)


    home_btn = Button(btn_label, text="Homepage", bg="Grey", fg="White", width=15, height=1, font=("Fira Code", 15),
                      command=home)
    home_btn.place(relx=0.2, rely=0.0)
    home_btn.bind("<Enter>", on_enter)
    home_btn.bind("<Leave>", on_leave)

    hom.mainloop()



def records():
    log.destroy()
    global rec
    rec = Toplevel()
    rec.state("zoomed")
    rec.title("Quizzical Suspects")

    # FRAMES:
    rec_mainframe = Frame(rec, bg="rosy brown", borderwidth=10, highlightthickness=2, relief=GROOVE)
    rec_mainframe.place(height=710, width=1367)

    img1 = PhotoImage(file=r'C:\Users\USER\Desktop\quiz\bg.png')
    img2 = img1.subsample(1, 1)
    l1 = Label(rec_mainframe, image=img2)
    l1.pack()

    record_frame = Frame(rec_mainframe, bg="White", borderwidth=10, highlightthickness=0)
    record_frame.place(x=45, y=40, width=1250, height=610)

    # LABELS:
    result_label = Label(record_frame, bg="White", text="PREVIOUS RECORD", fg="black",
                         font=("BookmanOldStyle 32 bold underline"))
    result_label.place(relx=0.34, rely=0.03)

    no_label = Label(record_frame, text="Test No", font=("TimesNewRoman", 15, "bold", "underline"), bg="white",
                     fg="black")
    no_label.place(relx=0.10, rely=0.18)

    total_label = Label(record_frame, text="Total Score", font=("TimesNewRoman", 15, "bold", "underline"), bg="white",
                        fg="black")
    total_label.place(relx=0.32, rely=0.18)

    score_label = Label(record_frame, text="Score Obtained", font=("TimesNewRoman", 15, "bold", "underline"),
                        bg="white", fg="black")
    score_label.place(relx=0.54, rely=0.18)

    status_label = Label(record_frame, text="Status", font=("TimesNewRoman", 15, "bold", "underline"), bg="white",
                         fg="black")
    status_label.place(relx=0.78, rely=0.18)

    username=ename.get()

    # Fetching Records Of User From Database:
    import pyodbc

    con = pyodbc.connect(r'DRIVER={Microsoft Access Driver (*.mdb, *.accdb)};'
                         r'DBQ=C:\Users\USER\Desktop\quiz\Quiz.accdb;')
    cur = con.cursor()
    record=cur.execute("Select * from Record where Username='"+ username +"'")
    data = record.fetchall()

    no = len(data)
    num=no-(no-(no-1))

    rec_entry_frame = Frame(record_frame, bg="White")
    rec_entry_frame.place(y=140, height=395, width=1230)

    if no>0:
        for i in data:
            no_show = Label(rec_entry_frame, text=no-num, font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                              width=17)
            no_show.grid(row=no, column=1, padx=50)

            total_show = Label(rec_entry_frame, text=i[1], font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                               width=17)
            total_show.grid(row=no, column=2, padx=40)

            score_show = Label(rec_entry_frame, text=i[2], font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                               width=17)
            score_show.grid(row=no, column=3, padx=40)

            status_show = Label(rec_entry_frame, text=i[3], font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                                width=17)
            status_show.grid(row=no, column=4)

            no = no + 1

    else:
        norecord_show = Label(rec_entry_frame,text="No Records!!", font=("Comic Sans MS", 18, "bold"), bg="white",
                              fg="Red",width=17)
        norecord_show.place(relx=0.38,rely=0.25)

    con.commit()
    con.close()

    # Button Commands:

    def logout():
        rec.destroy()

    def next():
        quiz_home()

    # Button hover effect:

    def on_enter(e):
        e.widget['background'] = 'purple'

    def on_leave(e):
        e.widget['background'] = 'grey'

    # BUTTONS:

    btn_label = Label(record_frame, bg="Plum")
    btn_label.pack(fill=X, ipady=12, side=BOTTOM)

    next_btn = Button(btn_label, text="Next", bg="grey", fg="white", width=15,
                      height=1, font=("Fira Code", 15), command=next)
    next_btn.place(relx=0.63)
    next_btn.bind("<Enter>", on_enter)
    next_btn.bind("<Leave>", on_leave)

    logout_btn = Button(btn_label, text="Logout", bg="grey", fg="white", width=15, height=1,
                      font=("Fira Code", 15), command=logout)
    logout_btn.place(relx=0.24)
    logout_btn.bind("<Enter>", on_enter)
    logout_btn.bind("<Leave>", on_leave)

    rec.mainloop()



def login():
    global log
    log = Toplevel()
    log.state("zoomed")
    log.title("Quizzical Suspects")

    # Data from user:
    global ename
    ename = StringVar()
    epassword = StringVar()

    # FRAMES:
    log_mainframe = Frame(log, bg="rosy brown", borderwidth=10, highlightthickness=2, relief=GROOVE)
    log_mainframe.place(height=710, width=1367)

    img1 = PhotoImage(file=r'C:\Users\USER\Desktop\quiz\bg.png')
    img2 = img1.subsample(1, 1)
    l1 = Label(log_mainframe, image=img2)
    l1.pack()

    log_frame = Frame(log_mainframe, bg="white", borderwidth=10, highlightthickness=0)
    log_frame.place(x=45, y=40, width=1250, height=610)

    # LABELS:
    login_label = Label(log_frame, text="LOGIN", font=("BookmanOldStyle 32 bold underline"), bg="white", fg="Black")
    login_label.place(relx=0.42, rely=0.15)

    name_label = Label(log_frame, text="USER NAME:", font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                       width=17)
    name_label.place(relx=0.25, rely=0.35)

    password_label = Label(log_frame, text="PASSWORD:", font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                           width=17)
    password_label.place(relx=0.25, rely=0.48)

    # ENTRY:
    name_entry = Entry(log_frame, textvariable=ename, font=("Arial", 15), fg="BLACK", width=25)
    name_entry.place(relx=0.43, rely=0.35)

    password_entry = Entry(log_frame, textvariable=epassword, font=("Arial", 15), fg="BLACK", width=25,
                           show="*")
    password_entry.place(relx=0.43, rely=0.48)

    # Button Commands:

    def homepage():
        log.destroy()

    # For Login:

    def login_btn():
        Username=ename.get()
        Password=epassword.get()

        if Username == "" or Password == "":
            error_label = Label(log_frame, text="ERROR! USERNAME AND PASSWORD REQUIRED",width=40, font=("Microsoft YaHei UI", 15),
                                bg="white", fg="red")
            error_label.place(relx=0.29, rely=0.6)
        else:
            con = pyodbc.connect(r'DRIVER={Microsoft Access Driver (*.mdb, *.accdb)};'
                                 r'DBQ=C:\Users\USER\Desktop\quiz\Quiz.accdb;')
            create = con.cursor()
            userdata = create.execute(
                "Select * from userdata where Username='" + Username + "' and Password='" + Password + "'")
            data = userdata.fetchall()
            print(data)

            if (len(data) > 0):
                records()

            else:
                error_label = Label(log_frame, text="INCORRECT USERNAME OR PASSWORD !",
                                    font=("Microsoft YaHei UI", 15),width=40,bg="white", fg="red")
                error_label.place(relx=0.30, rely=0.6)


    # Button hover effect:
    def on_enter(e):
        e.widget['background'] = 'purple'

    def on_leave(e):
        e.widget['background'] = 'grey'


    # BUTTONS:

    btn_label = Label(log_frame, bg="Plum")
    btn_label.pack(fill=X, ipady=12, side=BOTTOM)

    login_btn = Button(btn_label, text="Login", bg="grey", fg="white", width=15, height=1, font=("Fira Code", 15),
                       command=login_btn)
    login_btn.place(relx=0.65)
    login_btn.bind("<Enter>", on_enter)
    login_btn.bind("<Leave>", on_leave)

    home_btn = Button(btn_label, text="Home", bg="grey", fg="white", width=15, height=1, font=("Fira Code", 15),
                      command=homepage)
    home_btn.place(relx=0.2)
    home_btn.bind("<Enter>", on_enter)
    home_btn.bind("<Leave>", on_leave)

    log.mainloop()



def signup():
    global sig
    sig = Toplevel()
    sig.state("zoomed")
    sig.title("Quizzical Suspects")

    # FRAMES:
    sig_mainframe = Frame(sig,bg="rosy brown", borderwidth=10, highlightthickness=2, relief=GROOVE)
    sig_mainframe.place(height=710, width=1367)

    bg_img = PhotoImage(file=r'C:\Users\USER\Desktop\quiz\bg.png')
    bg_img_s = bg_img.subsample(1, 1)
    bg_img_l = Label(sig_mainframe, image=bg_img_s)
    bg_img_l.pack()

    sig_frame = Frame(sig_mainframe, bg="White", borderwidth=10, highlightthickness=0)
    sig_frame.place(x=45, y=40, width=1250, height=610)


    # LABELS:
    signup_label = Label(sig_frame,text="SIGNUP", font=("BookmanOldStyle 32 bold underline"), bg="white", fg="Black")
    signup_label.place(relx=0.42, rely=0.09)

    name_label = Label(sig_frame,text="FULL NAME:", font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                       width=17)
    name_label.place(relx=0.25, rely=0.25)

    username_label = Label(sig_frame,text="USER NAME:", font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                           width=17)
    username_label.place(relx=0.25, rely=0.35)

    password_label = Label(sig_frame,text="PASSWORD:", font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                           width=17)
    password_label.place(relx=0.25, rely=0.45)

    region_label = Label(sig_frame,text="REGION:", font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                         width=17)
    region_label.place(relx=0.235, rely=0.55)

    contact_label = Label(sig_frame,text="CONTACT:", font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                          width=17)
    contact_label.place(relx=0.24, rely=0.65)

    error_entry = Label(sig_frame,text="", font=("TimesNewRoman", 15, "bold"), bg="white", fg="black",
                       width=17)
    error_entry.place(relx=0.43, rely=0.75)

    #Data from user:
    fullname= StringVar()
    username= StringVar()
    password= StringVar()
    region= StringVar()
    contact= StringVar()

    # ENTRY:
    # fullname
    name_entry = Entry(sig_frame, textvariable=fullname, font=("Arial", 15), fg="BLACK", width=25)
    name_entry.place(relx=0.43, rely=0.25)

    # username
    username_entry = Entry(sig_frame, textvariable=username, font=("Arial", 15), fg="BLACK", width=25)
    username_entry.place(relx=0.43, rely=0.35)

    # password
    password_entry = Entry(sig_frame, textvariable=password, font=("Arial", 15), fg="BLACK", width=25)
    password_entry.place(relx=0.43, rely=0.45)

    # region
    region_entry = Entry(sig_frame, textvariable=region, font=("Arial", 15), fg="BLACK", width=25)
    region_entry.place(relx=0.43, rely=0.55)

    # contact
    contact_entry = Entry(sig_frame, textvariable=contact, font=("Arial", 15), fg="BLACK", width=25)
    contact_entry.place(relx=0.43, rely=0.65)

    # Button Commands:

    def back():
        sig.destroy()

    def login_page():
        sig.destroy()
        login()

    # For Signup:

    def add_to_database():
        Fullname = fullname.get()
        Username = username.get()
        Password = password.get()
        Region = region.get()
        Contact = contact.get()

        if Fullname == '' or Username == '' or Password == '' or Region == '' or Contact == '':
            error_entry = Label(sig_frame, text="WARNING! FILL THE EMPTY FIELDS!!!", font=("Microsoft YaHei UI", 16), bg="white", fg="red",
                                width=40)
            error_entry.place(relx=0.28, rely=0.75)

        else:
                con = pyodbc.connect(r'DRIVER={Microsoft Access Driver (*.mdb, *.accdb)};'
                                     r'DBQ=C:\Users\USER\Desktop\quiz\Quiz.accdb;')
                create= con.cursor()
                userdata = create.execute("Select * from userdata where username='"+Username+"'")
                data = userdata.fetchall()

                if (len(data) > 0):
                     error_entry = Label(sig_frame, text="WARNING! RECORD ALREADY EXISTS!!!", font=("Microsoft YaHei UI", 16),
                                         bg="white", fg="red",width=40)
                     error_entry.place(relx=0.28, rely=0.75)

                else:
                     print(len(data))
                     try:
                        create.execute(f"INSERT INTO userdata(Fullname,Username,Password,Region,Contact)values('{Fullname}','{Username}','{Password}','{Region}','{Contact}')")
                        con.commit()
                        sig.destroy()
                        messagebox.showinfo("Quizzical Suspects", "Signed Up Successfully")

                     except:
                         con.rollback()
                     finally:
                         create.close()
                         con.close()

    # Button hover effect:

    def on_enter(e):
        e.widget['background'] = 'purple'
    def on_leave(e):
        e.widget['background'] = 'grey'

    # BUTTONS:

    btn_label = Label(sig_frame, bg="Plum")
    btn_label.pack(fill=X, ipady=12, side=BOTTOM)

    back_btn = Button(btn_label, text="Back", bg="grey", fg="white", width=15, height=1, font=("Fira Code", 15),
                      command=back)
    back_btn.place(relx=0.12)
    back_btn.bind("<Enter>", on_enter)
    back_btn.bind("<Leave>", on_leave)

    signup_btn = Button(btn_label, text="SignUp", bg="grey", fg="white", width=15, height=1, font=("Fira Code", 15),
                        command=add_to_database)
    signup_btn.place(relx=0.72)
    signup_btn.bind("<Enter>", on_enter)
    signup_btn.bind("<Leave>", on_leave)

    account_btn = Button(btn_label, text="Already have an Account?", bg="grey", fg="white", height=1,
                         width=22,font=("Fira Code", 14), command=login_page)
    account_btn.place(relx=0.4)
    account_btn.bind("<Enter>", on_enter)
    account_btn.bind("<Leave>", on_leave)

    sig.mainloop()



tit=Tk()
tit.state("zoom")
tit.title("Quizzical Suspects")
tit.iconphoto(True,PhotoImage(file=r"C:\Users\USER\Desktop\quiz\quizlogo.png"))

# FRAMES
tit_mainframe = Frame(tit,bg="rosy brown", borderwidth=10, highlightthickness=2, relief=GROOVE)
tit_mainframe.place(height=710, width=1367)

bg_img=PhotoImage(file=r'C:\Users\USER\Desktop\quiz\bg.png')
bg_l=Label(tit_mainframe,image=bg_img)
bg_l.pack()

tit_frame=Frame(tit_mainframe, bg="white smoke", borderwidth=10, highlightthickness=0)
tit_frame.place(x=45, y=40, width=1250, height=610)

# Images:
quizsirenimg = PhotoImage(file=r'C:\Users\USER\Desktop\quiz\quiz_siren.png')
quizsirenimg_l = Label(tit_frame, image=quizsirenimg)
quizsirenimg_l.place(relx=0.07,rely=0.35)

manimg=PhotoImage(file=r'C:\Users\USER\Desktop\quiz\man.png')
manimg_s=manimg.subsample(1,1)
manimg_l = Label(tit_frame,image=manimg_s)
manimg_l.place(relx=0.33, rely=0.2)

onlinequizimg=PhotoImage(file=r'C:\Users\USER\Desktop\quiz\online_quiz.png')
onlinequizimg_s=onlinequizimg.subsample(1,1)
onlinequizimg_l = Label(tit_frame,image=onlinequizimg_s)
onlinequizimg_l.place(relx=0.7,rely=0.3)

# LABELS:
quizzical_label=Label(tit_frame,text="Quizzical Suspects",font=("Stencil 36 bold underline"),bg="white smoke",fg="black")
quizzical_label.place(relx=0.3,rely=0.04)


#Button Commands:

def gotologin():
    login()

def gotosignup():
    signup()

def exit():
    msg_box = messagebox.askquestion("Quizzical Suspects", "Are you sure you want to Exit?")
    if msg_box=='yes':
        tit.destroy()
    else:
        pass


# Button hover effect:

def on_enter(e):
    e.widget['background'] = 'purple'
def on_leave(e):
    e.widget['background'] = 'grey'


# BUTTONS:
btn_label=Label(tit_frame,bg="Plum")
btn_label.pack(fill=X,ipady=12,side=BOTTOM)

signup_btn=Button(btn_label,text="SignUp",bg="grey",fg="white",width=14,height=1,font=("Fira Code",15),command=gotosignup)
signup_btn.place(relx=0.12)
signup_btn.bind("<Enter>", on_enter)
signup_btn.bind("<Leave>", on_leave)

login_btn=Button(btn_label,text="Login",bg="grey",fg="white",width=14,height=1,font=("Fira Code",15),command=gotologin)
login_btn.place(relx=0.42)
login_btn.bind("<Enter>", on_enter)
login_btn.bind("<Leave>", on_leave)

exit_btn=Button(btn_label,text="Exit",bg="grey",fg="white",width=14,height=1,font=("Fira Code",15),command=exit)
exit_btn.place(relx=0.72)
exit_btn.bind("<Enter>", on_enter)
exit_btn.bind("<Leave>", on_leave)

tit.mainloop()



