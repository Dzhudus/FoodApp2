Profile Activity with Logout Functionality

This project implements a profile activity in an Android application with buttons to navigate to other activities (Favorites, Edit) and a logout functionality that clears the user session and redirects to the Welcome screen.
Features

    User Profile Card: Displays user name and email.
    Navigation Buttons:
        Favorite: Redirects to FavoritesActivity.
        Edit Recipe: Redirects to EditActivity.
        Logout: Clears user session and redirects to WelcomeActivity.

How to Use

    Clone the repository:

    git clone <repository-url>

    Open the project in Android Studio.

    Run the ProfileActivity to see the layout and interact with the buttons.

    Logout:
        Clicking the Logout button will:
            Clear the user session data (e.g., using SharedPreferences).
            Redirect to WelcomeActivity.
            Close the ProfileActivity to prevent users from going back to the profile screen.

Code Implementation
ProfileActivity.java

import android.content.Intent;
import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
import com.google.android.material.button.MaterialButton;

public class ProfileActivity extends AppCompatActivity {

    private MaterialButton favoriteButton;
    private MaterialButton editRecipeButton;
    private MaterialButton logoutButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_profile);

        // Initialize buttons
        favoriteButton = findViewById(R.id.favoriteButton);
        editRecipeButton = findViewById(R.id.editRecipeButton);
        logoutButton = findViewById(R.id.logoutButton);

        // Set up click listeners
        setUpButtonListeners();
    }

    private void setUpButtonListeners() {
        // Navigate to FavoritesActivity when "Favorite" button is clicked
        favoriteButton.setOnClickListener(v -> {
            Intent intent = new Intent(ProfileActivity.this, FavoritesActivity.class);
            startActivity(intent);
        });

        // Navigate to EditActivity when "Edit Recipe" button is clicked
        editRecipeButton.setOnClickListener(v -> {
            Intent intent = new Intent(ProfileActivity.this, EditActivity.class);
            startActivity(intent);
        });

        // Log out the user when "Logout" button is clicked
        logoutButton.setOnClickListener(v -> {
            // Clear user session data, e.g., shared preferences
            SharedPreferences sharedPreferences = getSharedPreferences("USER_SESSION", MODE_PRIVATE);
            sharedPreferences.edit().clear().apply();

            // Redirect to WelcomeActivity
            Intent intent = new Intent(ProfileActivity.this, WelcomeActivity.class);
            startActivity(intent);
            finish(); // Close ProfileActivity to prevent back navigation
        });
    }
}

Screenshots

    Profile screen with user details.
    Navigation buttons: Favorite, Edit, Logout.
    Logout redirects to the welcome screen.

License

This project is licensed under the MIT License.

Replace <repository-url> with the URL of your GitHub repository or the link to where your project is hosted. This README file provides a clear, concise overview of the project and its functionality, making it easier for others to understand and use.
