# Android-PopUp-Window-and-Changing-Variables

        iBLogo.setOnClickListener(new View.OnClickListener(){
            @Override
            public void onClick(View v){

                LayoutInflater layoutInflater
                        = (LayoutInflater)getBaseContext()
                        .getSystemService(LAYOUT_INFLATER_SERVICE);
                View popupView = layoutInflater.inflate(R.layout.popup, null);

                final PopupWindow popupWindow = new PopupWindow(
                        popupView,
                        DrawerLayout.LayoutParams.FILL_PARENT,
                        DrawerLayout.LayoutParams.FILL_PARENT);

                ConstraintLayout clk = (ConstraintLayout) popupView.findViewById(R.id.clNew);
                TextView popupText = (TextView) popupView.findViewById(R.id.textViewPop);
                ImageView popupImage = (ImageView) popupView.findViewById(R.id.imageViewPop);

                clk.setOnClickListener(new View.OnClickListener() {
                    @Override
                    public void onClick(View v) {

                        popupWindow.dismiss();
                    }
                });

                popupImage.setImageResource(R.drawable.ic_launcher);

                popupText.setText("hello");



                /*
                Button btnDismiss = (Button)popupView.findViewById(R.id.dismiss);
                btnDismiss.setOnClickListener(new Button.OnClickListener(){

                    @Override
                    public void onClick(View v){
                        // TODO Auto-generated method stub
                        popupWindow.dismiss();
                    }});*/

                popupWindow.showAsDropDown(iBLogo, 50, 50);
            }
        });
