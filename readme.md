1. copy the splash screen project to your main project path (the same path of solution file).
2. click add existing project from solution and add splash screen project by chossing the file SplashScreen.csproj.
3. from solution properties go to project dependencies and check SplashScreen project.
4. in your main project right click on references then add reference then from projects select SplashScreen as reference.
5. copy the image you want after rename it "screen" to the path "YOUR MAIN PROJECT"\bin\Debug\screen.jpg
6. in your main project edit the main method by copying and pastting the below code:

Note: just change msg to what you want and frmMain() to your main form

		Random r = new Random();
            int percent = 0;
            string msg = "Loading Monitor ";
            Application.EnableVisualStyles();
            Application.SetCompatibleTextRenderingDefault(false);
            SplashScreen.SplashScreen.ShowSplashScreen();
            Application.DoEvents();                   
            while (percent < 100)
            {
                percent = r.Next(percent, 100);
                SplashScreen.SplashScreen.SetStatus(msg + percent + "%");
                System.Threading.Thread.Sleep(r.Next(0, 1000));
                if (percent > 90)
                {
                    SplashScreen.SplashScreen.SetStatus(msg + "100%");
                    System.Threading.Thread.Sleep(1000);
                    break;
                }              
            }
            Application.Run(new frmMain());