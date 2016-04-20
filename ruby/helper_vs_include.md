###Helper vs include

The method helper_method is to explicitly share some methods defined in the controller to make them available for the view. This is used for any method that you need to access from both controllers and helpers/views (standard helper methods are not available in controllers). e.g. common use case:

#application_controller.rb

  ```
  def current_user
    @current_user ||= User.find_by_id!(session[:user_id])
  end
  helper_method :current_user
  ```

the helper method on the other hand, is for importing an entire helper to the views provided by the controller (and it's inherited controllers). What this means is doing

  ```
  # application_controller.rb
  helper :all
  For Rails > 3.1

  # application.rb
  config.action_controller.include_all_helpers = true
  # This is the default anyway, but worth knowing how to turn it off
  ```
makes all helper modules available to all views (at least for all controllers inheriting from application_controller.

  ```
  # home_controller.rb
  helper UserHelper
  ```

makes the UserHelper methods available to views for actions of the home controller. This is equivalent to doing:
  ```
  # HomeHelper
  include UserHelper
  ```

