<template>
  <div
    class="topNav"
    :class="{ topNavBarColor: barColor }"
  >
    <div class="side">
      <font-awesome-icon
        class="menuIcon navIcon"
        icon="bars"
        role="button"
        tabindex="0"
        @click="toggleSideNav"
        @keypress="toggleSideNav"
      />
      <font-awesome-icon
        class="navBackIcon navIcon"
        icon="arrow-left"
        role="button"
        tabindex="0"
        @click="historyBack"
        @keypress="historyBack"
      />
      <font-awesome-icon
        class="navForwardIcon navIcon"
        icon="arrow-right"
        role="button"
        tabindex="0"
        @click="historyForward"
        @keypress="historyForward"
      />
      <font-awesome-icon
        class="navSearchIcon navIcon"
        icon="search"
        role="button"
        tabindex="0"
        @click="toggleSearchContainer"
        @keypress="toggleSearchContainer"
      />
      <div class="logo">
        <div
          class="logoIcon"
        />
        <div
          class="logoText"
        />
      </div>
    </div>
    <div class="middle">
      <div class="searchContainer">
        <ft-input
          :placeholder="$t('Search / Go to URL')"
          class="searchInput"
          :is-search="true"
          :data-list="searchSuggestionsDataList"
          @input="getSearchSuggestionsDebounce"
          @click="goToSearch"
        />
        <font-awesome-icon
          class="navFilterIcon navIcon"
          icon="filter"
          role="button"
          tabindex="0"
          @click="showFilters = !showFilters"
          @keypress="showFilters = !showFilters"
        />
      </div>
      <ft-search-filters
        v-show="showFilters"
        class="searchFilters"
        :class="{ expand: !isSideNavOpen }"
      />
    </div>
    <ft-profile-selector class="side profiles" />
  </div>
</template>

<script src="./top-nav.js" />
<style scoped lang="sass" src="./top-nav.sass" />
