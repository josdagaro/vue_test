<template>
  <div class="container">
    <div class="panel panel-primary">
      <div class="panel-heading">Hotel Management</div>
      <div class="panel-body">
        <fieldset class="col-md-4">
          <legend>{{ title }}</legend>
          <div class="panel panel-default">
            <div class="panel-body">
              <form>
                <div class="form-group">
                  <label for="name">Name</label>
                  <input type="text" class="form-control" id="name" aria-describedby="nameHelper" placeholder="Enter name">
                  <small id="nameHelper" class="form-text text-muted">It have to be an unique name.</small>
                </div>
                <div class="form-group">
                  <label for="location">Location</label>
                  <input type="text" class="form-control" id="location" aria-describedby="locationHelper" placeholder="Enter location">
                  <small id="locationHelper" class="form-text text-muted">Please, enter an unique place.</small>
                </div>
                <div class="btn-group">
                  <button type="submit" class="btn btn-primary mb-2">{{ action }}</button>
                  <button type="reset" class="btn btn-default mb-2">Clean</button>
                </div>
              </form>
            </div>
          </div>
        </fieldset>
        <fieldset class="col-md-8">
          <legend>Records</legend>
          <div class="panel panel-default">
            <div class="panel-body">
              <HotelsGrid />
              <HotelsPagination
                :maxVisibleButtons=3
                :totalPages=5
                :total=50
                :currentPage=1
                />
            </div>
          </div>
        </fieldset>
        <div class="clearfix"></div>
      </div>
    </div>
  </div>
</template>

<script>
import HotelsGrid from './Grid.vue'
import HotelsPagination from './Pagination.vue'

export default {
  name: 'HotelsForm',
  props: {
    title: String,
    action: String
  },
  components: {
    HotelsGrid,
    HotelsPagination
  }
}
</script>
