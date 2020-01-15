# Android

## Calculator Project



* MainActivity_java

```java
package com.example.calculator;

import androidx.appcompat.app.AppCompatActivity;


import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {
    final String TAG = "CALCULATOR";

    int buttonResourceIds [] = {
            R.id.btn_0, R.id.btn_1, R.id.btn_2, R.id.btn_3,
            R.id.btn_4, R.id.btn_5, R.id.btn_6,
            R.id.btn_7, R.id.btn_8, R.id.btn_9,
            R.id.btn_plus,R.id.btn_minus,R.id.btn_multi,R.id.btn_div
    };

    EditText et_result;
    EditText et_result_1;
    Button btn_clear;
    Button btn_enter;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        et_result = findViewById(R.id.et_result);

        et_result_1 = findViewById(R.id.et_result_1);

        btn_clear = (Button) findViewById(R.id.btn_clear);
        btn_clear.setOnClickListener(mClickListener);

        btn_enter = (Button) findViewById(R.id.btn_enter);
        btn_enter.setOnClickListener((mClickListener));

        for(int rId : buttonResourceIds) {
            final Button btn = (Button) findViewById(rId);
            Log.d(TAG, "Button=" + btn);

            btn.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    et_result.setText(String.valueOf(et_result.getText().toString() + btn.getText().toString()));
                }
            });
        }
    }

    View.OnClickListener mClickListener = new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            switch (v.getId()) {
                //clear
                case R.id.btn_clear:
                    et_result.setText("");
                    et_result_1.setText("");
                    break;
                case R.id.btn_enter:
                    String rowData = et_result.getText().toString();
                    Log.v(TAG, "[btn_enter] rowData=" + rowData);
                    String [] operator = new String[15];

                    String [] data = rowData.split("X|/|-|\\+");

                    int index = 0;

                    for(char c : rowData.toCharArray()) {
                        switch (c) {
                            case 1:
                                Log.d(TAG, "num=" + c);
                                break;
                            case 'X' :
                                Log.d(TAG, "X operator" + c);

                                int multi = 0;
                                int mumtiTemp = 0;
                                for(String r : data) {
                                    Log.v(TAG, "Number=" + r);
                                    multi = Integer.parseInt(r);
                                    mumtiTemp = multi;
                                    Log.d(TAG, "multi=" + multi);
                                }
                                multi = multi * mumtiTemp;
                                Log.d(TAG, "multi=" + multi);
                                et_result_1.setText(Integer.toString(multi));
                                break;
                            case '/' :
                                Log.d(TAG, "/ operator" + c);

                                int div = 0;
                                for(String r : data) {
                                    Log.v(TAG, "Number=" + r);
                                    div = div / Integer.parseInt(r);
                                    Log.d(TAG, "div=" + div);
                                }
                                et_result_1.setText(Integer.toString(div));
                                break;
                            case '+' :
                                Log.d(TAG, "+ operator" + c);

                                int sum = 0;
                                for(String r : data) {
                                    Log.v(TAG, "Number=" + r);
                                    sum = sum + Integer.parseInt(r);
                                    Log.d(TAG, "sum=" + sum);
                                }
                                et_result_1.setText(Integer.toString(sum));

//                                et_result_1.setText(et_result.getText());
                                break;
                            case '-' :
                                Log.d(TAG, "- operator" + c);

                                int sub = 0;
                                for(String r : data) {
                                    Log.v(TAG, "Number=" + r);
                                    sub = sub - Integer.parseInt(r);
                                    Log.d(TAG, "sub=" + sub);
                                }
                                et_result_1.setText(Integer.toString(sub));
                                operator[index] = String.valueOf(c);
                                index++;
                                break;
                        }
                    }
//                    int sum = 0;
//                    for(String r : data) {
//                        Log.v(TAG, "Number=" + r);
//                        sum = sum + Integer.parseInt(r);
//                        Log.d(TAG, "sum=" + sum);
//                    }
//                    et_result_1.setText(Integer.toString(sum));

//                    et_result_1.setText(Integer.parseInt(et_result.getText().toString()));
//                    et_result_1.setText(et_result.getText());
                    break;
            }
        }
    };
}

```

```java
package com.example.calculator;

import androidx.appcompat.app.AppCompatActivity;


import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import java.util.LinkedList;

public class MainActivity extends AppCompatActivity {
    final String TAG = "CALCULATOR";

    int buttonResourceIds [] = {
            R.id.btn_0, R.id.btn_1, R.id.btn_2, R.id.btn_3,
            R.id.btn_4, R.id.btn_5, R.id.btn_6,
            R.id.btn_7, R.id.btn_8, R.id.btn_9,
            R.id.btn_plus,R.id.btn_minus,R.id.btn_multi,R.id.btn_div
    };

    EditText et_result;
    EditText et_result_1;
    Button btn_clear;
    Button btn_enter;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        et_result = findViewById(R.id.et_result);

        et_result_1 = findViewById(R.id.et_result_1);

        btn_clear = (Button) findViewById(R.id.btn_clear);
        btn_clear.setOnClickListener(mClickListener);

        btn_enter = (Button) findViewById(R.id.btn_enter);
        btn_enter.setOnClickListener((mClickListener));

        for(int rId : buttonResourceIds) {
            final Button btn = (Button) findViewById(rId);
            Log.d(TAG, "Button=" + btn);

            btn.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    et_result.setText(String.valueOf(et_result.getText().toString() + btn.getText().toString()));
                }
            });
        }
    }

    View.OnClickListener mClickListener = new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            switch (v.getId()) {
                //clear
                case R.id.btn_clear:
                    et_result.setText("");
                    et_result_1.setText("");
                    break;
                case R.id.btn_enter:
                    //문자열로 받은 숫자와 연산자롤 각각 linkedList 에 저장
                    LinkedList<Integer> numList = new  LinkedList<Integer>();
                    LinkedList<Character> opList = new LinkedList<Character>();

                    String rowData = et_result.getText().toString();
                    Log.v(TAG, "[btn_enter] rowData=" + rowData);
                    String num ="";

                    for(int i = 0; i<rowData.length(); i++){
                        char c = rowData.charAt(i);

                        if(c == '+' || c == '-' || c == '*' || c == '/'){
                            numList.add(Integer.parseInt(num));
                            opList.add(c);
                            Log.v(TAG, "[btn_enter] op=" + c);
                            num ="";
                            continue;
                        }
                        num += c;
                        Log.v(TAG, "[btn_enter] num= " + num);
                    }
                    numList.add(Integer.parseInt(num));
                    Log.v(TAG, "[btn_enter] numList=" + numList);
                    Log.v(TAG, "[btn_enter] opList=" + opList);

                    while (!opList.isEmpty()){
                        Log.v(TAG, "[btn_enter] while opList=" + opList);
                        int prevNum = numList.poll();
                        Log.v(TAG, "[btn_enter] while prevNum=" + prevNum);
                        int nextNum = numList.poll();
                        Log.v(TAG, "[btn_enter] while nextNum=" + nextNum);
                        char op = opList.poll();

                        if(op == '+') {
                            numList.addFirst(prevNum + nextNum);
                            Log.v(TAG, "[btn_enter] while numList=" + numList);
                        } else if(op == '-') {
                            numList.addFirst(prevNum - nextNum);
                        } else if(op == '*') {
                            numList.addFirst(prevNum * nextNum);
                        } else if(op == '/') {
                            numList.addFirst(prevNum / nextNum);
                        }
                    }

                    et_result_1.setText(numList.poll());
                    Log.v(TAG, "[btn_enter] final="  );
                    break;
            }
        }
    };
}
```

* eclipse test file

```java
package calcul;

import java.util.LinkedList;
import java.util.Scanner;

public class Calcul {

	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		
		LinkedList<Integer> numList = new LinkedList<Integer>(); //숫자관련
        LinkedList<Character> opList = new LinkedList<Character>(); //연산자 관련
        
        
        String input = scan.nextLine(); //enter까지 포함한 것까지 입력
        String num = ""; //연사자 외에 숫자들을 임시 저장할 곳
        
        for(int i = 0; i < input.length(); i++) {
            char ch = input.charAt(i); //string을 char 타입 단위로 나눔
            
          //  System.out.println("ch="+i+"-"+ch);
            
            if(ch == '+' || ch =='-' || ch == '*' || ch == '/') {
            	//System.out.println("num="+num);
                numList.add(Integer.parseInt(num)); //숫자로 바꿔서 숫자배열에 추가
              //  System.out.println("chOper="+ch);
                opList.add(ch); //연산자를 연산자배열에 추가
                num = ""; //임시로 저장된 숫자를 비워준다           
                continue; //제일 가까운 명령문으로 이동
            }
            num += ch; //연산자 앞까지의 숫자를 임시로 넣어 놓음
          //  System.out.println();
        }
        numList.add(Integer.parseInt(num)); //마지막 숫자
        int multi = numList.get(1) * numList.get(2);
        numList.remove(1);
        numList.remove(1);
        numList.add(1, multi);
        opList.remove(1);
        
        System.out.println(numList);
        System.out.println(opList);
 
        while(!opList.isEmpty()) { //연산자배열이 빌 때까지
            int prevNum = numList.poll(); //poll : 앞부터 완전히 뺀다
            int nextNum = numList.poll();
            char op = opList.poll();
            
            System.out.println("prevNum ="+prevNum);
            System.out.println("nextNum ="+nextNum);
            
            // / * + / //
//            for(int i = 0; i<opList.size(); i++) {
//            	if(op == '*') {
//            		
//            	}
//            }
            
            
            
            if(op == '+') {
                numList.addFirst(prevNum + nextNum); //addFirst 배열 제일 앞에 넣는다
            } else if(op == '-') {
                numList.addFirst(prevNum - nextNum);
            } else if(op == '*') {
                numList.addFirst(prevNum * nextNum);
            } else if(op == '/') {
                numList.addFirst(prevNum / nextNum);
            }
        }
        System.out.println(numList.poll());
	}
}

```

[LInked List 자료](https://eskeptor.tistory.com/89)



* EditText 수정, 연산자 우선순위 진행

```java
package com.example.calculator;

import androidx.appcompat.app.AppCompatActivity;


import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import java.util.LinkedList;

public class MainActivity extends AppCompatActivity {
    final String TAG = "CALCULATOR";

    int buttonResourceIds [] = {
            R.id.btn_0, R.id.btn_1, R.id.btn_2, R.id.btn_3,
            R.id.btn_4, R.id.btn_5, R.id.btn_6,
            R.id.btn_7, R.id.btn_8, R.id.btn_9,
            R.id.btn_plus,R.id.btn_minus,R.id.btn_multi,R.id.btn_div
    };

    EditText et_result;
    EditText et_result_1;
    Button btn_clear;
    Button btn_enter;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        et_result = findViewById(R.id.et_result);

        et_result_1 = findViewById(R.id.et_result_1);

        btn_clear = (Button) findViewById(R.id.btn_clear);
        btn_clear.setOnClickListener(mClickListener);

        btn_enter = (Button) findViewById(R.id.btn_enter);
        btn_enter.setOnClickListener((mClickListener));

        for(int rId : buttonResourceIds) {
            final Button btn = (Button) findViewById(rId);
            Log.d(TAG, "Button=" + btn);

            btn.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    et_result.setText(String.valueOf(et_result.getText().toString() + btn.getText().toString()));
                }
            });
        }
    }

    View.OnClickListener mClickListener = new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            switch (v.getId()) {
                //clear
                case R.id.btn_clear:
                    et_result.setText("");
                    et_result_1.setText("");
                    break;
                case R.id.btn_enter:
                    //문자열로 받은 숫자와 연산자롤 각각 linkedList 에 저장
                    LinkedList<Integer> numList = new  LinkedList<Integer>();
                    LinkedList<Character> opList = new LinkedList<Character>();

                    String rowData = et_result.getText().toString();  //입렵 받은 값을 String  type 으로
                    Log.v(TAG, "[btn_enter] rowData=" + rowData);
                    String num ="";  //문자열에서 정수 값을 얻어내는 변수

                    for(int i = 0; i<rowData.length(); i++){
                        char c = rowData.charAt(i); //문자열을 하나의 문자로 쪼갠다.
                        //정수와 연산자를 각 List 에 담는다
                        if(c == '+' || c == '-' || c == '*' || c == '/'){
                            numList.add(Integer.parseInt(num));
                            opList.add(c);
                            Log.v(TAG, "[btn_enter] op=" + c);
                            num ="";
                            continue;
                        }
                        num += c;
                        Log.v(TAG, "[btn_enter] num= " + num);
                    }
                    numList.add(Integer.parseInt(num));
                    Log.v(TAG, "[btn_enter] numList=" + numList);
                    Log.v(TAG, "[btn_enter] opList=" + opList);

                    int indexCount = 0;

                    while (!opList.isEmpty()){

                        Log.v(TAG, "[btn_enter] while opList=" + opList);
                        int prevNum = numList.poll();
                        Log.v(TAG, "[btn_enter] while prevNum=" + prevNum);
                        int nextNum = numList.poll();
                        Log.v(TAG, "[btn_enter] while nextNum=" + nextNum);
                        char op = opList.poll();

                        for(int i = 0; i<opList.size(); i++){
                            indexCount++;
                            if(op == '*'){
                                numList.add(i, numList.get(i)*numList.get(i+1));
                                numList.remove(i+1);
                                numList.remove(i+2);
                            }
                        }

                        if(op == '+') {
                            numList.addFirst(prevNum + nextNum);
                            Log.v(TAG, "[btn_enter] while numList=" + numList);
                        } else if(op == '-') {
                            numList.addFirst(prevNum - nextNum);
                        } else if(op == '*') {
                            numList.addFirst(prevNum * nextNum);
                        } else if(op == '/') {
                            numList.addFirst(prevNum / nextNum);
                        }
                    }

                    et_result_1.setText(Integer.toString(numList.poll())); // EditText 는 문 자형을 받기때문에 numList에 담긴 정수를 toString 함수를 이요해서 문자열로 변환 해줘야한다.
                    Log.v(TAG, "[btn_enter] final=" + numList);
                    break;
            }
        }
    };
}

```
