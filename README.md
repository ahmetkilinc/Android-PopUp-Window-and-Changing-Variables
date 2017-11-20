# Android-PopUp-Window-and-Changing-Variables

        import java.util.Random;
        import android.widget.Button;
        import android.view.LayoutInflater;
        import android.view.View;
        import android.support.constraint.ConstraintLayout;
        import android.view.Window;
        
        ...

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

                Random rand = new Random(); // random number generator.
                int rndInt = rand.nextInt(5) + 1; // we have 5 images so we generate 5 numbers.

                String imgName = "img" + rndInt;
                int id = getResources().getIdentifier(imgName, "drawable", getPackageName());
                popupImage.setImageResource(id); // adding random image resource to image.

                ConstraintLayout clk = (ConstraintLayout) popupView.findViewById(R.id.clNew);
                TextView popupText = (TextView) popupView.findViewById(R.id.textViewPop);
                ImageView popupImage = (ImageView) popupView.findViewById(R.id.imageViewPop);

                popupText.setText("hello");


                clk.setOnClickListener(new View.OnClickListener() {
                    @Override
                    public void onClick(View v) {

                        popupWindow.dismiss();
                    }
                });

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
