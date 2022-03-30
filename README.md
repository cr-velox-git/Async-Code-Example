/** Async-Code-Example
Async Code java
**/

public class AsyncTaskTestActivity extends Activity {

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);  

        // This starts the AsyncTask
        // Doesn't need to be in onCreate()
        new MyTask().execute("my string parameter");
    }

    // Here is the AsyncTask class:
    //
    // AsyncTask<Params, Progress, Result>.
    //    Params – the type (Object/primitive) you pass to the AsyncTask from .execute() 
    //    Progress – the type that gets passed to onProgressUpdate()
    //    Result – the type returns from doInBackground()
    // Any of them can be String, Integer, Void, etc. 

    private class MyTask extends AsyncTask<String, Integer, String> {

        // Runs in UI before background thread is called
        @Override
        protected void onPreExecute() {
            super.onPreExecute();

            // Do something like display a progress bar
        }

        // This is run in a background thread
        @Override
        protected String doInBackground(String... params) {
            // get the string from params, which is an array
            String myString = params[0];

            // Do something that takes a long time, for example:
            for (int i = 0; i <= 100; i++) {

                // Do things

                // Call this to update your progress
                publishProgress(i);
            }

            return "this string is passed to onPostExecute";
        }

        // This is called from background thread but runs in UI
        @Override
        protected void onProgressUpdate(Integer... values) {
            super.onProgressUpdate(values);

            // Do things like update the progress bar
        }

        // This runs in UI when background thread finishes
        @Override
        protected void onPostExecute(String result) {
            super.onPostExecute(result);

            // Do things like hide the progress bar or change a TextView
        }
    }
}

Flow Chat

![AV5YR](https://user-images.githubusercontent.com/48889698/160756821-105c89f8-6d3f-415e-a438-d429e0433238.png)
