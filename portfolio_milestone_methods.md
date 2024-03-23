# Portfolio Milestone

**Brian Gunther**  
Colorado State University Global  
CSC320: Programming I  
Dr. Gonzalez  
March 24, 2024

The goal of this milestone submission is to introduce the methods of the Automobile and AutomobileInventory classes using Pseudocode. This will ultimately function as an inventory program for a car dealership, per the Portfolio project requirements.

To maintain focus on the methods, the program logic and declaration of variables are implied or abstracted rather than stated in detail.

## Methods for Class: Automobile

The purpose of this class is to hold attributes of a single vehicle, like its vin, make, model, color, and other inherent details. It also contains public methods to construct the object and to update mutable attributes.

### Default Constructor Method
Set private class fields to default values

```pseudocode
public Automobile() {
   SET: this.vin TO ""
   SET: this.make TO ""
   SET: this.model TO ""
   SET: this.color TO ""
   SET: this.year TO -1
   SET: this.mileage TO 0
}
```

### Parameterized Constructor Method
Set private class fields to parameter values

```pseudocode
public Automobile(String vin, String make, String model, String color, int year, int mileage) {
   SET: this.vin TO vin
   SET: this.make TO make
   SET: this.model TO model
   SET: this.color TO color
   SET: this.year TO year
   SET: this.mileage TO mileage
}
```

### Update Color Attribute
Set private class field to parameter value
```pseudocode
public void updateColor(String color) {
   SET: this.color TO color
}
```

### Update Mileage Attribute
Set private class field to parameter value

```pseudocode
public void updateMileage(int mileage) {
   SET: this.mileage TO mileage
}
```

### Get VIN
Return the value of private field "vin"

```pseudocode
public String getVin() {
   RETURN: this.vin
}
```

## Methods for Class: AutomobileInventory

The purpose of this class is to provide a user interface for accessing and using the inventory. This class will contain an ArrayList of type Automobile which holds the objects.

### Add New Vehicle
Return a new vehicle object with the instance fields populated (additional program logic will add this object to the inventory array)

```pseudocode
public Automobile addVehicle(String vin, String make, String model, String color, int year, int mileage) {
   TRY:
      SEARCH inventory for vin
      IF vin does not already exist:
            INSTANTIATE a new object "automobile" of type Automobile using the provided parameters
            RETURN automobile
      ELSE:
         RETURN null
   EXCEPT:
      Log exception
      RETURN null
}
```

### Remove a Vehicle
Remove a vehicle from inventory arraylist based on its vin

```pseudocode
public boolean removeVehicle(String vin) {
   TRY:
      SEARCH inventory arraylist for the vin
      IF found:
            DELETE vehicle from arraylist
            RETURN True
      ELSE:
         RETURN False
   EXCEPT:
      Log exception
      RETURN False
}
```

### Retrieve Vehicle Information
Return an object corresponding to the provided vin

```pseudocode
public Automobile showVehicle(String vin) {
   INSTANTIATE a new empty Automobile object "automobile"
   TRY:
      SEARCH inventory arraylist for the vin provided and store in "automobile"
      IF found:
         RETURN automobile
      ELSE:
         RETURN null
   EXCEPT:
      Log exception
      RETURN null
}
```

### Update Vehicle Attributes (String overload)
Update **String** attributes per user preference.

**Note:** Only the mutable attributes like mileage and color can change. The Vin, Year, Make, Model should never change.

```pseudocode
public boolean updateAttribute(String vin, String attribute, String value) {
   TRY:
      SEARCH inventory arraylist for the vin
      IF found:
         VALIDATE attribute, RETURN False if invalid

         SWITCH attribute:
            color:   CALL updateColor
            default: RETURN False

         RETURN True
      ELSE:
         RETURN False
   EXCEPT:
      Log exception
      RETURN False
}
```

### Update Vehicle Attributes (Integer overload)
Update **integer** attributes per user preference.

**Note:** Only the mutable attributes like mileage and color can change. The Vin, Year, Make, Model should never change.

```pseudocode
public boolean updateAttribute(String vin, String attribute, int value) {
   TRY:
      SEARCH inventory arraylist for the vin
      IF found:
         VALIDATE attribute, RETURN False if invalid

         SWITCH attribute:
            mileage:   CALL updateMileage
            default: RETURN False

         RETURN True
      ELSE:
         RETURN False
   EXCEPT:
      Log exception
      RETURN False
}
```

### List All Vehicles
Retrieve and print each vehicle in formatted output

```pseudocode
public void showAllVehicles() {
   TRY:
      FOR EACH Automobile object in the arraylist:
         PRINT LINE: Vin, Make, Model, Color, Year, Mileage
   EXCEPT:
      Log exception
}
```
