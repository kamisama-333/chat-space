## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false,unique:true|
|name|string|null: false|
### Association
- has_many :groups_users
- has_many :messages
- has_many :groups,through:groups_users

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false,unique:true|
### Association
- has_many :groups_users
- has_many :users,through:groups_users
- has_many :messages

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user















-# .credit-update
-#   .credit-update__label
-#     クレジットカード情報入力
-#   .card-form
-#     .card-form__box
-#       = form_tag(cards_path, method: :post, id: 'charge-form', name: "inputForm") do |f|
-#         .card-form__box__number
-#           %label{class:'box-group--label', for: 'card_number'} カード番号
-#           %span.input-require
-#             必須
-#           = text_field_tag "number", "", class: 'card-number--input', type: "text", id: 'card_number', maxlength: "16", placeholder: "半角数字のみ"
-#           .registration-error{type: "hidden", value: "必須項目です"}
          
-#         .card-form__box__expire
-#           %label.box-group--label 有効期限
-#           %span.input-require
-#             必須
-#           .card-expire
-#             .card-expire__select-month
-#               %select#exp_month{name: "exp_month", type: "text"}
-#                 %option{value: "1"}01
-#                 %option{value: "2"}02
-#                 %option{value: "3"}03
-#                 %option{value: "4"}04
-#                 %option{value: "5"}05
-#                 %option{value: "6"}06
-#                 %option{value: "7"}07
-#                 %option{value: "8"}08
-#                 %option{value: "9"}09
-#                 %option{value: "10"}10
-#                 %option{value: "11"}11
-#                 %option{value: "12"}12
-#               %i.card-form-expire-icon
               
-#               %span{class: "month"} 月
-#             .card-expire__select-year
-#               %select#exp_year{name: "exp_year", type: "text"}
-#                 %option{value: "2019"}19
-#                 %option{value: "2020"}20
-#                 %option{value: "2021"}21
-#                 %option{value: "2022"}22
-#                 %option{value: "2023"}23
-#                 %option{value: "2024"}24
-#                 %option{value: "2025"}25
-#                 %option{value: "2026"}26
-#                 %option{value: "2027"}27
-#                 %option{value: "2028"}28
-#                 %option{value: "2029"}29
-#               %i.card-form-expire-icon
                
-#               %span{class:"year"} 年

-#         .card-form__box__security-code
-#           %label.box-group--label{for: "cvc"} セキュリティーコード
-#           %span.input-require
-#             必須
-#           = text_field_tag "cvc", "", class: 'payment__security-code', type: "text", id: "cvc", maxlength: "4" ,placeholder: "カード背面４桁もしくは３桁の番号"
-#           .question-form
-#             %span.question-form__mark ?
-#             %span.question-form__text 
-#               カード裏面の番号とは？
-#         #card_token
-#           = submit_tag "追加する", class: "card-form__box__add", id: "token_submit", type: 'button'






















.card-group
  .card-group__title
    %label クレジットカード情報
    %br
  .card-group__boxs
    .card-group__boxs__information
      .card-group__boxs__information__bango
        カード番号
      .card-group__boxs__information__number
        = "***** **** **** ****"
      -# = "**** **** **** " + @default_card_information.last4
      %br
      .card-group__boxs__information__valid
        有効期限
      .card-group__boxs__information__year-month
        = "12/20"
      -# - exp_month = @default_card_information.exp_month.to_s
      -# - exp_year = @default_card_information.exp_year.to_s.slice(2,3)
      -# = exp_month + " / " + exp_year
      -# = form_tag(card_path, method: :delete, id: 'charge-form',  name: "inputForm") do
      .button-delate
        %input{ type: "hidden", name: "card_id", value: "" }
        %button.button-delate__name  削除する




















.credit-update {
  display: block;
  background: $light-gray;
  

  &__label {
    background-color: #fff;
    margin: auto;
    padding: 24px 8px;
    text-align: center;
    font-size: 18px;
    border-bottom: solid 1px #cccccc;
    font-weight: 600;
    width: 700px;
  }
  .card-form {
    padding: 24px 16px 40px;
    background-color: #fff;
    width: 700px;
    margin: auto;

    &__box {
      max-width: 343px;
      margin: auto;


      &__number {
        width: 100%;
        margin: 20px 0 0;

        .box-group--label {
          font-weight: 600;

        }

        .input-require {
          margin: 0 0 0 8px;
          padding: 2px 4px;
          color: white;
          background-color: red;
        }

        .card-number--input {
          width: 100%;
          margin: 8px 0 0;
          height: 48px;
          padding: 10px 16px 8px;
          font-size: 16px;
        }
      }

      &__expire {
        margin: 40px 0 0;

        .box-group--label {
          font-weight: 600;
        }


        .input-require  {
          margin: 0 0 0 8px;
          padding: 2px 4px;
          color: white;
          background-color: red;
        }


        .card-expire  {
          margin: 8px 0 0;
          
          &__select-month {
            display: table-cell;
            text-align: left;
            width: 170px;
            
  
            #exp_month {
              height: 48px;
              width: calc(100% - 38px);
              font-size: 16px;
              cursor: pointer;
            }
          }

          &__select-year {
            display: table-cell;
            text-align: right;
            width: 170px;
          
            #exp_year {
              height: 48px;
              width: calc(100% - 38px);
              font-size: 16px;
              cursor: pointer;
            }
          }
        }
      }


      &__security-code {
        width: 100%;
        margin: 40px 0 0;


        .box-group--label {
          font-weight: 600;
        }


        .input-require {
          margin: 0 0 0 8px;
          padding: 2px 4px;
          color: white;
          background-color: red;
        }


        .payment__security-code {
        width: 100%;
        margin: 8px 0 0;
        height: 48px;
        padding: 10px 16px 8px;
        font-size: 16px;
        }

        .question-form {
          margin: 8px 0 0;
          text-align: right;
          color: #0099e8;

          &__mark {
            display: inline-block;
            width: 14px;
            height: 14px;
            border-radius: 50%;
            background: #0099e8;
            color: #fff;
            line-height: 14px;
            font-size: 12px;
            text-align: center;
          }
        }
      }


      #card_token {
        margin: 40px 0 0;
        


        .card-form__box__add  {
          -webkit-appearance: none;
          width: 100%;
          height: 48px;
          font-size: 14px;
          color: white;
          cursor: pointer;
          background: #ea352d;

        }
      }
    }
  }
}














// show---------------------------------------------------

.card-group {
  display: block;
  background: $light-gray;


  &__title {
    background-color: #fff;
    margin: auto;
    padding: 24px 8px;
    text-align: center;
    font-size: 18px;
    border-bottom: solid 1px #cccccc;
    font-weight: 600;
    width: 700px;


  }

  &__boxs {
    padding: 50px 16px 40px;
    background-color: #fff;
    width: 700px;
    margin: auto;

    &__information {
      max-width: 343px;
      margin: auto;

      &__bango {
        display: table-cell;
        text-align: left;
        width: 120px;
        font-weight: 600;
      }

        &__number {
          margin: 8px 0 0;
          padding: 10px 16px 8px;
          font-size: 25px;
          text-align: center;
          height: 110px;
          display: table-cell;
          position: relative;
          top: 10px;
        }

      &__valid {
        display: table-cell;
        width: 130px;
        font-weight: 600;
      }

      &__year-month {
        margin: 8px 0 0;
        padding: 10px 16px 8px;
        font-size: 20px;
        text-align: center;
        height: 110px;
        display: table-cell;

      }



      .button-delate {
        margin: 40px 0 0;
        height: 100px;


        &__name {
          -webkit-appearance: none;
          width: 100%;
          height: 48px;
          font-size: 14px;
          color: white;
          cursor: pointer;
          background: #ea352d;
        }


      }
    }
  }
}