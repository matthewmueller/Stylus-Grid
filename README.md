# Stylus Grid System

This is the gird system file used on WomStreet. It makes it easy to
create quick grids that can be edited. It borrows heavily from the
inspirations set by [960.gs](http://960.gs). The reason you might choose
to use it is that it can be re-generated for any number of columns and
a width of your chosing, all handled at compilation time by stylus


## Quick Reference

    #The following variables should be set to your choosing

    $gridWidth = 1140px  # The total grid width of the content area
    $gridNumColumns = 24 # The number of columns used in the grid
    $gutterWidth = 20px  # The space between grid columns

    # Available Mixins

    container()          # A parent element for columns. Centers itself
                         # in the page and adheres to max width set 
                         # above


    column($num)         # Creates a column of the number passed in

    column-push($num,    # Offsets a column by the number of columns
                $alpha)  # passed in. Also needs to know if the offset
                         # should be considered "alpha" 

    centered()           # Centers a column in its container

    alpha()              # Used to cancel the margin on the left, 
                         # required for the first column in a
                         # container

    omega() / last()     # Used to cancel the margin on the right,  
                         # required for the last column in a
                         # container


## Usage

Usage of the grid is very similar to [960.gs](http://960.gs). 

### Containers

All grid elements should be in a container element. A container centers
itself within the page and adheres to the max width set by `$gridWidth`.

### Columns

A column is set by using the `column(n)` mixin. 

You can also offset a column by a certain number of columns by using
`column-push(n)`. Note that `column-push` must be mixed in *after*
`column`. If you use `column-push`, it can take an additional argument
for whether the column-push should be alpha'd (see alpha and omega
below)


### Alpha and Omega

Just like 960.gs, the first column in a row should include alpha and the last
column should include omega. This enables nesting of columns.


### Centering

You can center a column inside its container by mixing in `center()`.



### Quick example


sample.html

    <html>
      <body>
        <div class="page-section">
          <div class="third">
            <h1>This is a third</h1>
          </div>
          <div class="third">
            <h1>This is a third</h1>
          </div>
          <div class="third">
            <h1>This is a third</h1>
          </div>
        </div>
      </body>
    </html>


sample.styl

    @include 'stylus-grid'

    body
      container()

    .page-section
      column(12)
      column-push(12, true);
    
    .page-section-third
      column(4)

      &:first-of-type
        alpha()

      &:last-of-type
        omega()


