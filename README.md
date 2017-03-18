# Android Code Snippets
The are common Android code snippets that I occasionally need a refresh on without a whole tutorial.

<table>
  <!--Titles row-->
  <tr>
      <th>Use</th>
      <th>Code</th>
      <th>Notes</th>
  </tr>
  
  <!--row 1-->
  <tr>
    <td>Simple Toast</td>
    <td>
      <pre lang="java">
        Toast.makeText(getActivity(), "This is a Toast!", 
        Toast.LENGTH_LONG).show();
      </pre>
    </td>
    <td>Replace with Toast.LENGTH_SHORT to display for a short period.</td>
  </tr>
  
  <!--row 2-->
  <tr>
    <td>Simple Dialog</td>
    <td>
      <pre lang="java">
        new AlertDialog.Builder(context)
          .setTitle("The Title")
          .setMessage("This is the message")
          .setPositiveButton("Positive", new DialogInterface.OnClickListener() {
            public void onClick(DialogInterface dialog, int id) { 
                //Positive
            }
          })
          .setNegativeButton("Negative", new DialogInterface.OnClickListener() {
            public void onClick(DialogInterface dialog, int id) { 
                //Negative
            }
          })
          .setIcon(android.R.drawable.ic_dialog_alert)
          .show();
      </pre>
    </td>
    <td>Need AlertDialog.Builder(className.this) if within a listener.</td>
  </tr>
  
  <!--row 3-->
  <tr>
    <td>Run something after X milliseconds delay</td>
    <td>
      <pre lang="java">
        final Handler handler = new Handler();
        handler.postDelayed(new Runnable() {
          @Override
          public void run() {
            //Do something after 1000ms (1s)
          }
        }, 1000);
      </pre>
    </td>
    <td></td>
  </tr>
  
  <!--row 4-->
  <tr>
    <td>Thread with Handler</td>
    <td>
      <pre lang="java">
        Handler handler = new Handler(){
          @Override
          public void handleMessage(Object obj){
            //Do something with the obj
          }
        };
        Thread thread = new Thread() {
          @Override
          public void run(){
            Object obj = threadWork();
            handler.handleMessage(obj)
          }   
        };
      </pre>
    </td>
    <td>To do something in a thread then pass it to UI thread using handler</td>
  </tr>
  
  <!--row 5-->
  <tr>
    <td>Setting SharedPreferences</td>
    <td>
      <pre lang="java">
        SharedPreferences.Editor editor = getSharedPreferences("PREFS_NAME", MODE_PRIVATE).edit();
        editor.putString("Key", "Value");
        editor.putInt("ID", 1);
        editor.apply();
      </pre>
    </td>
    <td>apply() is asynchronous call to perform disk I/O where as commit() is synchronous. So avoid calling commit() from the UI thread.</td>
  </tr>
  
  <!--row 6-->
  <tr>
    <td>Setting SharedPreferences</td>
    <td>
      <pre lang="java">
        SharedPreferences prefs = getSharedPreferences("PREFS_NAME", MODE_PRIVATE); 
        String valueString = prefs.getString("Key", "Default");
        int idInt = prefs.getInt("ID", 0);
      </pre>
    </td>
    <td></td>
  </tr>
  
  <!--row 7-->
  <tr>
    <td>New Intent With Extra</td>
    <td>
      <pre lang="java">
        Intent intent = new Intent(this, NewActivity.class);
        String extraString = "extra";
        intent.putExtra("extraKey", extraString);
        startActivity(intent);
        //Get Extra in the NewActivity
        Intent intent = getIntent();
        if (intent != null)
          String extraStringGot = intent.getStringExtra("extraKey");
      </pre>
    </td>
    <td></td>
  </tr>
</table>
