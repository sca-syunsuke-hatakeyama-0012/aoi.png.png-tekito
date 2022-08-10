# aoi.png.png-tekito
/*
プロジェクト名

ミニゲーム

３０ゲームを作る

aoi.png.png

熊谷柊哉
畠山駿佑
佐々木祐路


#include <iostream>
#include"math.h"
#include"stdlib.h"
#include"time.h"
using namespace std;
int num1, num2 = 1,num3,num4,nanid,teban,r,i;
int getturn;
int pl, last=30;
bool AIflg=true,playerflg;



int main(void)
{
    if (nanid == 0)
    {
        srand((unsigned int)time(NULL));//乱数をリセット
        for (int i = 0; i < 1; i++)
        {
            getturn = (int)(rand() % 4+1);//先手後手
        }
    }
        cout << "ルール説明\n" << endl;
        cout << "プレイヤーとAIは交互に数字を１から順番に言います。\n" << endl;
        cout << "３０を言ったら負けとなります。\n" << endl;
        cout << "1度のターンでは連続した数字を最大で3つまでいうことができます。\n" << endl;
        cout << "３よりも大きい数を入力した場合は３になります\n" << endl;
        cout << "難易度を選択してください\n";
        cout << "特別モードを遊びたい場合は３を選んでください。" << endl;
        cout << "1，簡単。2，難しい。" << endl;
        cin >> nanid;//難易度の設定
                if (nanid > 3)
                {
     nanid = 3;
                }
    if (nanid == 1)//難易度が簡単であった場合
    {
        while (num3 <last)//最後の値よりも小さい間はループ
        {

            srand((unsigned int)time(NULL));//乱数をリセット
            for ( i = 0; i < 1; i++)
            {
                r = (int)(rand() % 3 + 1);//AIが追加する数を抽選（１～３）
            }
            if (0<getturn&&getturn<=2)//ゲットターンの値が０より大きく、２以下なら
            {
                playerflg = true;//プレイヤーが先手
                AIflg = false;
                getturn = 0;//ゲットターンの値を０に
            }
          if (0<getturn >=3)//ゲットターンの値が３か４なら
            {
              AIflg = true;//AIが先手
               playerflg = false;
                getturn = 0;//ゲットターンの値を０に
            }
             if (AIflg && num3 >= last-4 && num3 < last-1)//AIがこのターンで勝てるなら
             {
                 num3 = last - 1;//AIが最後の値から１引いた値を宣言
                 cout << "AI「" << last-1 << "」" << endl;
                 cout << "プレイヤー「"<<last <<"」"<< endl;//プレイヤーが最後の数字を言う
                 cout << "AI「あなたの負けです」" << endl;//AIによる勝利宣言
                 return 0;//プログラム終了
             }
             else if (num3 == last-1) //最後の値より1少ない値なら
             {
                 cout << "AI「" << last << "」" << endl;//AIが最後の数字を言う
                 num3 = last;
                 cout << "AI「あなたの勝利です。」" << endl;//AIによる敗北宣言
                 return 0;//プログラム終了
             }
             else  if (AIflg)//上記の条件に当てはまらないかつ、AIのターンならば
             {
                num3 += r;//AIの値を決定
                cout <<"AI「"<< num3 <<"」"<< endl;//AIの値を出力
                i = 0;//
                playerflg = true;//プレイヤーのターン
                AIflg = false;
            }
             if (playerflg)//プレイヤーのターン
            {
                cout << "加算する値を入力してください" << endl;
                cin >> num1;
                if (num1 > 3)//入力した値が３よりも大きいなら
                {
                    num1=r;//加算する値がランダムに
                }
                num3 += num1;//現在の値に加算
                cout << "プレイヤー「" << num3 << "」" << endl;//現在の値を出力
                AIflg = true;//AIのターン
                playerflg = false;
            }
        }
    }
    else  if (nanid == 2)//難易度が難しいならば
    {
        cout << "AI「１」\n";//AIの値宣言
        if (num2 < 29)//ゲームが終わっていないなら
        {
            while (num2 < last-1)//最後の値から１引いた値よりも現在の値が小さいならループ
            {
                srand((unsigned int)time(NULL));//乱数の値をリセット
                for (i = 0; i < 1; i++)
                {
                    r = (int)(rand() % 3 + 1);//乱数の範囲設定（１～３）
                }
                cout << "いくつ加算するのか入力してください" << endl;
                cin >> num1;//加算する値を決定
                if (num1 > 3)//加算する値が３より大きいなら
                {
                    num1 = r;//加算する値をランダムに
                }
                num3 = num1;//加算する値を一度別の変数に代入して保存
                num2 += num1;//現在の値に加算
                cout << "プレイヤー「" << num2 << "」" << endl;//プレイヤーによる現在の値の宣言
                while (num3 < 4)//プレイヤーの加算した値が４になるまで
                {
                    num3 += 1;//加算した値+1
                    num2 += 1;//AIが加算する値+1
                }
                cout << "AI「" << num2 << "」" << endl;//AIによる現在の値の宣言
            }
        }
        if (num2 >= 29)//ゲームの終了が確定したら
        {
            cout << "プレイヤー「"<<last<<"」" << endl;//最後の値をプレイヤーが宣言
            cout << "AI「残念でしたね。あなたの負けです。」\n" << endl;//AIによる勝利宣言
        }
    }
    if (nanid == 3)//特別モードならば
    {
        cout << "言ってしまうと負けの数字を設定してくださいしてください" << endl;
        cin >>last;//最後の値を決定
        cout << "1度に加算できる数の最大数を入力してください" << endl;
        cin >> pl;//１度に加算できる最大数を決定
        while (num3 < last)//最後の値よりも現在の値がちいさいなら
        {
            //以下難易度簡単と同じ
            srand((unsigned int)time(NULL));
            for (i = 0; i < 1; i++)
            {
                r = (int)(rand() % pl + 1);
            }
            if (0 < getturn && getturn <= 2)
            {
                playerflg = true;
                AIflg = false;
                getturn = 0;
            }
            if (0 < getturn >= 3)
            {
                AIflg = true;
                playerflg = false;
                getturn = 0;
            }
            if (AIflg && num3 >= last - (pl+1) && num3 < last - 1)
            {
                cout << "AI「" << last - 1 << "」" << endl;
                cout << "プレイヤー「" << last << "」" << endl;
                cout << "AI「あなたの負けです」" << endl;
                return 0;
            }
            else if (num3 == last - 1)
            {
                cout << "AI「" << last << "」" << endl;
                num3 = last;
                cout << "AI「あなたの勝利です。」" << endl;
                return 0;
            }
            else  if (AIflg)
            {
                num3 += r;
                cout << "AI「" << num3 << "」" << endl;
                i = 0;
                playerflg = true;
                AIflg = false;
            }

            if (playerflg)
            {
                cout << "加算する値を入力してください" << endl;
                cin >> num1;
                if (num1 > pl)
                {
                    num1 = r;
                }
                num3 += num1;
                cout << "プレイヤー「" << num3 << "」" << endl;
                AIflg = true;
                playerflg = false;
            }
        }
    }
}