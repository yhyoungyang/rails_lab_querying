# Rails Lab Querying

This is a [Rails app](https://github.com/WDI-HK-7/rails_lab_querying) for the owner of a tow lot to keep track of tow trucks and towed vehicles.

### Install Instructions

- [Fork the repo](https://github.com/WDI-HK-7/rails_lab_querying)!
- Create a new gemset for


```
$ bundle install
$ rake db:setup     # create the database and load this data
$ rails console
```

### Schema.rb

###### Tow Trucks

`Tow trucks` have a `make`, `model`, `year`, an `acquisition date`, the date when it was last `serviced`, the `mileage` and a text field for `notes`.

```ruby
  create_table "tow_trucks", force: true do |t|
    t.text    "make"
    t.text    "model"
    t.integer "year"
    t.date    "acquired_at"
    t.date    "last_service_at"
    t.integer "mileage"
    t.text    "notes"
  end
```

###### Vehicles

`Vehicles` have a `make`, `model`, and `color` (text), `year` (integer), `VIN` (unique non-nullable indexed text), a `category` (car/motorcycle/truck?), an `acquisition date`, a `release date`, a boolean indicating whether the towing fee has been `paid` and a text field for `notes`.

```ruby
  create_table "vehicles", force: true do |t|
    t.text    "make"
    t.text    "model"
    t.text    "color"
    t.integer "year"
    t.text    "vin",         null: false
    t.text    "category",    null: false
    t.date    "acquired_at"
    t.date    "released_at"
    t.decimal "fee",         precision: 8, scale: 2
    t.boolean "is_paid"
    t.text    "notes"
  end
```

### Exercises

The owner of the **Tow Lot** app has some questions about the data that is now entered into it.

Write a *single* ActiveRecord query to achieve each of the following objectives. Record your finished queries in a separate file.

**Note:** "Vehicle" here only refers to records in the `vehicles` table (i.e. not tow trucks).

1. Get a list of all tow trucks.
2. Get the vehicle with ID 3.
3. Get the vehicle with VIN D0985DF1593A350A4.
4. Get a list of all vehicles sorted by acquisition date.
5. Get a list of all silver vehicles, ordered alphabetically by make.
6. Get a list of all red Honda vehicles that are cars.
7. Get a count of all vehicles that are motorcycles.
8. Get a count of vehicles that are currently on the lot (i.e. not released).
9. Get a list of all tow trucks whose mileage is over 200,000.
10. Get a list of all tow trucks whose last service was more than 8 months ago.
11. Get the average tow fee across all vehicles.
12. Get the top 3 vehicles with the highest tow fees.
13. Get all vehicles that have a fee assessed which has not been paid.
14. Get a list of all released vehicles, sorted by most recently released.
15. Get a list of all vehicles that have notes.
16. Get the VINs of all vehicles manufactured before the year 2000.
17. Get the make, model, and year of all silver vehicles, ordered by year.
18. Get the total income from all vehicles (i.e. sum of all fees that are paid).

##### Bonus Points

The motorcycle business is going well, so the owner is frequently sorting and filtering by vehicle category. Add an index on this column to make these operations faster, and make it non-nullable to ensure all vehicles are categorized.
