<template>
	<div>
        <DataTableSubMenu />

		<div class="content-section introduction">
			<div class="feature-intro">
				<h1>DataTable - Scroll</h1>
				<p>Data scrolling is available horizontally, vertically or both. Virtual Scrolling mode is also provided to deal with large datasets by loading data on demand during scrolling.</p>
			</div>
		</div>

		<div class="content-section implementation">
            <h3>Vertical</h3>
			<DataTable :value="cars" :scrollable="true" scrollHeight="200px" :loading="loading">
                <Column field="vin" header="Vin"></Column>
                <Column field="year" header="Year"></Column>
                <Column field="brand" header="Brand"></Column>
                <Column field="color" header="Color"></Column>
            </DataTable>

            <h3>Virtual Scroll</h3>
			<DataTable :value="lazyCars" :scrollable="true" scrollHeight="200px" :lazy="true" :rows="20" :loading="loading"
                :virtualScroll="true" :virtualRowHeight="30" @virtual-scroll="onVirtualScroll" :totalRecords="lazyTotalRecords">
                <Column field="vin" header="Vin">
                    <template #loading>
                        <span class="loading-text"></span>
                    </template>
                </Column>
                <Column field="year" header="Year">
                    <template #loading>
                        <span class="loading-text"></span>
                    </template>
                </Column>
                <Column field="brand" header="Brand">
                    <template #loading>
                        <span class="loading-text"></span>
                    </template>
                </Column>
                <Column field="color" header="Color">
                    <template #loading>
                        <span class="loading-text"></span>
                    </template>
                </Column>
            </DataTable>

            <h3>Horizontal and Vertical</h3>
            <DataTable :value="cars" :scrollable="true" scrollHeight="200px" style="width: 600px" :loading="loading">
                <Column field="vin" header="Vin" headerStyle="width: 250px" columnKey="vin_1"></Column>
                <Column field="year" header="Year" headerStyle="width: 250px" columnKey="year_1"></Column>
                <Column field="brand" header="Brand" headerStyle="width: 250px" columnKey="brand_1"></Column>
                <Column field="color" header="Color" headerStyle="width: 250px" columnKey="color_1"></Column>
                <Column field="vin" header="Vin" headerStyle="width: 250px" columnKey="vin_2"></Column>
                <Column field="year" header="Year" headerStyle="width: 250px" columnKey="year_2"></Column>
                <Column field="brand" header="Brand" headerStyle="width: 250px" columnKey="brand_2"></Column>
                <Column field="color" header="Color" headerStyle="width: 250px" columnKey="color_2"></Column>
            </DataTable>

            <h3>Frozen Rows</h3>
            <DataTable :value="cars" :frozenValue="frozenCars" :scrollable="true" scrollHeight="200px" :loading="loading">
                <Column field="vin" header="Vin"></Column>
                <Column field="year" header="Year"></Column>
                <Column field="brand" header="Brand"></Column>
                <Column field="color" header="Color"></Column>
            </DataTable>

            <h3>Frozen Columns</h3>
            <DataTable :value="cars" :scrollable="true" scrollHeight="200px" frozenWidth="300px" :loading="loading">
                <Column field="vin" header="Vin" headerStyle="width: 300px" columnKey="vin_1" :frozen="true">
                    <template #body="slotProps">
                        <span style="font-weight: bold">{{slotProps.data.vin}}</span>
                    </template>
                </Column>
                <Column field="year" header="Year" headerStyle="width: 300px" columnKey="year_1"></Column>
                <Column field="brand" header="Brand" headerStyle="width: 300px" columnKey="brand_1"></Column>
                <Column field="color" header="Color" headerStyle="width: 300px" columnKey="color_1"></Column>
                <Column field="year" header="Year" headerStyle="width: 300px" columnKey="year_2"></Column>
                <Column field="brand" header="Brand" headerStyle="width: 300px" columnKey="brand_2"></Column>
                <Column field="color" header="Color" headerStyle="width: 300px" columnKey="color_2"></Column>
                <Column field="year" header="Year" headerStyle="width: 300px" columnKey="year_3"></Column>
                <Column field="brand" header="Brand" headerStyle="width: 300px" columnKey="brand_3"></Column>
                <Column field="color" header="Color" headerStyle="width: 300px" columnKey="color_3"></Column>
            </DataTable>
		</div>

        <div class="content-section documentation">
            <TabView>
                <TabPanel header="Source">
<CodeHighlight>
<template v-pre>
&lt;h3&gt;Vertical&lt;/h3&gt;
&lt;DataTable :value="cars" :scrollable="true" scrollHeight="200px" :loading="loading"&gt;
    &lt;Column field="vin" header="Vin"&gt;&lt;/Column&gt;
    &lt;Column field="year" header="Year"&gt;&lt;/Column&gt;
    &lt;Column field="brand" header="Brand"&gt;&lt;/Column&gt;
    &lt;Column field="color" header="Color"&gt;&lt;/Column&gt;
&lt;/DataTable&gt;

&lt;h3&gt;Virtual Scroll&lt;/h3&gt;
&lt;DataTable :value="lazyCars" :scrollable="true" scrollHeight="200px" :lazy="true" :rows="20" :loading="loading"
    :virtualScroll="true" :virtualRowHeight="30" @virtual-scroll="onVirtualScroll" :totalRecords="lazyTotalRecords"&gt;
    &lt;Column field="vin" header="Vin"&gt;
        &lt;template #loading&gt;
            &lt;span class="loading-text"&gt;&lt;/span&gt;
        &lt;/template&gt;
    &lt;/Column&gt;
    &lt;Column field="year" header="Year"&gt;
        &lt;template #loading&gt;
            &lt;span class="loading-text"&gt;&lt;/span&gt;
        &lt;/template&gt;
    &lt;/Column&gt;
    &lt;Column field="brand" header="Brand"&gt;
        &lt;template #loading&gt;
            &lt;span class="loading-text"&gt;&lt;/span&gt;
        &lt;/template&gt;
    &lt;/Column&gt;
    &lt;Column field="color" header="Color"&gt;
        &lt;template #loading&gt;
            &lt;span class="loading-text"&gt;&lt;/span&gt;
        &lt;/template&gt;
    &lt;/Column&gt;
&lt;/DataTable&gt;

&lt;h3&gt;Horizontal and Vertical&lt;/h3&gt;
&lt;DataTable :value="cars" :scrollable="true" scrollHeight="200px" style="width: 600px" :loading="loading"&gt;
    &lt;Column field="vin" header="Vin" headerStyle="width: 250px" columnKey="vin_1"&gt;&lt;/Column&gt;
    &lt;Column field="year" header="Year" headerStyle="width: 250px" columnKey="year_1"&gt;&lt;/Column&gt;
    &lt;Column field="brand" header="Brand" headerStyle="width: 250px" columnKey="brand_1"&gt;&lt;/Column&gt;
    &lt;Column field="color" header="Color" headerStyle="width: 250px" columnKey="color_1"&gt;&lt;/Column&gt;
    &lt;Column field="vin" header="Vin" headerStyle="width: 250px" columnKey="vin_2"&gt;&lt;/Column&gt;
    &lt;Column field="year" header="Year" headerStyle="width: 250px" columnKey="year_2"&gt;&lt;/Column&gt;
    &lt;Column field="brand" header="Brand" headerStyle="width: 250px" columnKey="brand_2"&gt;&lt;/Column&gt;
    &lt;Column field="color" header="Color" headerStyle="width: 250px" columnKey="color_2"&gt;&lt;/Column&gt;
&lt;/DataTable&gt;

&lt;h3&gt;Frozen Rows&lt;/h3&gt;
&lt;DataTable :value="cars" :frozenValue="frozenCars" :scrollable="true" scrollHeight="200px" :loading="loading"&gt;
    &lt;Column field="vin" header="Vin"&gt;&lt;/Column&gt;
    &lt;Column field="year" header="Year"&gt;&lt;/Column&gt;
    &lt;Column field="brand" header="Brand"&gt;&lt;/Column&gt;
    &lt;Column field="color" header="Color"&gt;&lt;/Column&gt;
&lt;/DataTable&gt;

&lt;h3&gt;Frozen Columns&lt;/h3&gt;
&lt;DataTable :value="cars" :scrollable="true" scrollHeight="200px" frozenWidth="300px" :loading="loading"&gt;
    &lt;Column field="vin" header="Vin" headerStyle="width: 300px" columnKey="vin_1" :frozen="true"&gt;
        &lt;template #body="slotProps"&gt;
            &lt;span style="font-weight: bold"&gt;&#123;&#123;slotProps.data.vin&#125;&#125;&lt;/span&gt;
        &lt;/template&gt;
    &lt;/Column&gt;
    &lt;Column field="year" header="Year" headerStyle="width: 300px" columnKey="year_1"&gt;&lt;/Column&gt;
    &lt;Column field="brand" header="Brand" headerStyle="width: 300px" columnKey="brand_1"&gt;&lt;/Column&gt;
    &lt;Column field="color" header="Color" headerStyle="width: 300px" columnKey="color_1"&gt;&lt;/Column&gt;
    &lt;Column field="year" header="Year" headerStyle="width: 300px" columnKey="year_2"&gt;&lt;/Column&gt;
    &lt;Column field="brand" header="Brand" headerStyle="width: 300px" columnKey="brand_2"&gt;&lt;/Column&gt;
    &lt;Column field="color" header="Color" headerStyle="width: 300px" columnKey="color_2"&gt;&lt;/Column&gt;
    &lt;Column field="year" header="Year" headerStyle="width: 300px" columnKey="year_3"&gt;&lt;/Column&gt;
    &lt;Column field="brand" header="Brand" headerStyle="width: 300px" columnKey="brand_3"&gt;&lt;/Column&gt;
    &lt;Column field="color" header="Color" headerStyle="width: 300px" columnKey="color_3"&gt;&lt;/Column&gt;
&lt;/DataTable&gt;
</template>
</CodeHighlight>

<CodeHighlight lang="javascript">
import CarService from '../../service/CarService';

export default {
    data() {
        return {
            cars: null,
            frozenCars: null,
            lazyCars: null,
            lazyTotalRecords: 0,
            loading: false
        }
    },
    carService: null,
    inmemoryData: null,
    created() {
        this.carService = new CarService();

        this.inmemoryData = [
            {"brand": "VW", "year": 2012, "color": "Orange"},
            {"brand": "Audi", "year": 2011, "color": "Black"},
            {"brand": "Renault", "year": 2005, "color": "Gray"},
            {"brand": "BMW", "year": 2003, "color": "Blue"},
            {"brand": "Mercedes", "year": 1995, "color": "Orange"},
            {"brand": "Volvo", "year": 2005, "color": "Black"},
            {"brand": "Honda", "year": 2012, "color": "Yellow"},
            {"brand": "Jaguar", "year": 2013, "color": "Orange"},
            {"brand": "Ford", "year": 2000, "color": "Black"},
            {"brand": "Fiat", "year": 2013, "color": "Red"},
            {"brand": "VW", "year": 2012, "color": "Orange"},
            {"brand": "Audi", "year": 2011, "color": "Black"},
            {"brand": "Renault", "year": 2005, "color": "Gray"},
            {"brand": "BMW", "year": 2003, "color": "Blue"},
            {"brand": "Mercedes", "year": 1995, "color": "Orange"},
            {"brand": "Volvo", "year": 2005, "color": "Black"},
            {"brand": "Honda", "year": 2012, "color": "Yellow"},
            {"brand": "Jaguar", "year": 2013, "color": "Orange"},
            {"brand": "Ford", "year": 2000, "color": "Black"},
            {"brand": "Fiat", "year": 2013, "color": "Red"},
            {"brand": "VW", "year": 2012, "color": "Orange"},
            {"brand": "Audi", "year": 2011, "color": "Black"},
            {"brand": "Renault", "year": 2005, "color": "Gray"},
            {"brand": "BMW", "year": 2003, "color": "Blue"},
            {"brand": "Mercedes", "year": 1995, "color": "Orange"},
            {"brand": "Volvo", "year": 2005, "color": "Black"},
            {"brand": "Honda", "year": 2012, "color": "Yellow"},
            {"brand": "Jaguar", "year": 2013, "color": "Orange"},
            {"brand": "Ford", "year": 2000, "color": "Black"},
            {"brand": "Fiat", "year": 2013, "color": "Red"},
            {"brand": "VW", "year": 2012, "color": "Orange"},
            {"brand": "Audi", "year": 2011, "color": "Black"},
            {"brand": "Renault", "year": 2005, "color": "Gray"},
            {"brand": "BMW", "year": 2003, "color": "Blue"},
            {"brand": "Mercedes", "year": 1995, "color": "Orange"},
            {"brand": "Volvo", "year": 2005, "color": "Black"},
            {"brand": "Honda", "year": 2012, "color": "Yellow"},
            {"brand": "Jaguar", "year": 2013, "color": "Orange"},
            {"brand": "Ford", "year": 2000, "color": "Black"},
            {"brand": "Fiat", "year": 2013, "color": "Red"}
        ];
    },
    mounted() {
        this.loading = true;

        setTimeout(() => {
            this.carService.getCarsLarge().then(data => {
                this.cars = data
                this.loading = false;
            });
        }, 150);

        this.frozenCars = [
            {brand: "BMW", year: 2013, color: "Grey", vin: "fh2uf23"},
            {brand: "Chevrolet", year: 2011, color: "Black", vin: "4525g23"}
        ];

        setTimeout(() => {
            this.lazyCars = this.loadChunk(0, 40);
            this.lazyTotalRecords = 250000;
        }, 250);
    },
    methods: {
          loadChunk(index, length) {
            let chunk = [];
            for (let i = 0; i &lt; length; i++) {
                chunk[i] = {...this.inmemoryData[i], ...{vin: (index + i)}};
            }

            return chunk;
        },
        onVirtualScroll(event) {
            /*
                For demo purposes keep loading the same dataset,
                in a real production application, this data should come from server by building the query with LazyLoadEvent options
            */
            setTimeout(() => {
                //last chunk
                if (event.first === 249980)
                    this.lazyCars = this.loadChunk(event.first, 20)
                else
                    this.lazyCars = this.loadChunk(event.first, event.rows)
            }, 250);
        }
    }
}
</CodeHighlight>

<CodeHighlight lang="css">
.loading-text {
    display: block;
    background-color: #f1f1f1;
    min-height: 19px;
    animation: pulse 1s infinite ease-in-out;
    text-indent: -99999px;
    overflow: hidden;
}
</CodeHighlight>
                </TabPanel>
            </TabView>
        </div>
	</div>
</template>

<script>
import CarService from '../../service/CarService';
import DataTableSubMenu from './DataTableSubMenu';

export default {
    data() {
        return {
            cars: null,
            frozenCars: null,
            lazyCars: null,
            lazyTotalRecords: 0,
            loading: false
        }
    },
    carService: null,
    inmemoryData: null,
    created() {
        this.carService = new CarService();

        this.inmemoryData = [
            {"brand": "VW", "year": 2012, "color": "Orange"},
            {"brand": "Audi", "year": 2011, "color": "Black"},
            {"brand": "Renault", "year": 2005, "color": "Gray"},
            {"brand": "BMW", "year": 2003, "color": "Blue"},
            {"brand": "Mercedes", "year": 1995, "color": "Orange"},
            {"brand": "Volvo", "year": 2005, "color": "Black"},
            {"brand": "Honda", "year": 2012, "color": "Yellow"},
            {"brand": "Jaguar", "year": 2013, "color": "Orange"},
            {"brand": "Ford", "year": 2000, "color": "Black"},
            {"brand": "Fiat", "year": 2013, "color": "Red"},
            {"brand": "VW", "year": 2012, "color": "Orange"},
            {"brand": "Audi", "year": 2011, "color": "Black"},
            {"brand": "Renault", "year": 2005, "color": "Gray"},
            {"brand": "BMW", "year": 2003, "color": "Blue"},
            {"brand": "Mercedes", "year": 1995, "color": "Orange"},
            {"brand": "Volvo", "year": 2005, "color": "Black"},
            {"brand": "Honda", "year": 2012, "color": "Yellow"},
            {"brand": "Jaguar", "year": 2013, "color": "Orange"},
            {"brand": "Ford", "year": 2000, "color": "Black"},
            {"brand": "Fiat", "year": 2013, "color": "Red"},
            {"brand": "VW", "year": 2012, "color": "Orange"},
            {"brand": "Audi", "year": 2011, "color": "Black"},
            {"brand": "Renault", "year": 2005, "color": "Gray"},
            {"brand": "BMW", "year": 2003, "color": "Blue"},
            {"brand": "Mercedes", "year": 1995, "color": "Orange"},
            {"brand": "Volvo", "year": 2005, "color": "Black"},
            {"brand": "Honda", "year": 2012, "color": "Yellow"},
            {"brand": "Jaguar", "year": 2013, "color": "Orange"},
            {"brand": "Ford", "year": 2000, "color": "Black"},
            {"brand": "Fiat", "year": 2013, "color": "Red"},
            {"brand": "VW", "year": 2012, "color": "Orange"},
            {"brand": "Audi", "year": 2011, "color": "Black"},
            {"brand": "Renault", "year": 2005, "color": "Gray"},
            {"brand": "BMW", "year": 2003, "color": "Blue"},
            {"brand": "Mercedes", "year": 1995, "color": "Orange"},
            {"brand": "Volvo", "year": 2005, "color": "Black"},
            {"brand": "Honda", "year": 2012, "color": "Yellow"},
            {"brand": "Jaguar", "year": 2013, "color": "Orange"},
            {"brand": "Ford", "year": 2000, "color": "Black"},
            {"brand": "Fiat", "year": 2013, "color": "Red"}
        ];
    },
    mounted() {
        this.loading = true;

        setTimeout(() => {
            this.carService.getCarsLarge().then(data => {
                this.cars = data
                this.loading = false;
            });
        }, 150);

        this.frozenCars = [
            {brand: "BMW", year: 2013, color: "Grey", vin: "fh2uf23"},
            {brand: "Chevrolet", year: 2011, color: "Black", vin: "4525g23"}
        ];

        setTimeout(() => {
            this.lazyCars = this.loadChunk(0, 40);
            this.lazyTotalRecords = 250000;
        }, 250);
    },
    methods: {
          loadChunk(index, length) {
            let chunk = [];
            for (let i = 0; i < length; i++) {
                chunk[i] = {...this.inmemoryData[i], ...{vin: (index + i)}};
            }

            return chunk;
        },
        onVirtualScroll(event) {
            /*
                For demo purposes keep loading the same dataset,
                in a real production application, this data should come from server by building the query with LazyLoadEvent options
            */
            setTimeout(() => {
                //last chunk
                if (event.first === 249980)
                    this.lazyCars = this.loadChunk(event.first, 20)
                else
                    this.lazyCars = this.loadChunk(event.first, event.rows)
            }, 250);
        }
    },
    components: {
        'DataTableSubMenu': DataTableSubMenu
    }
}
</script>

<style lang="scss" scoped>
.loading-text {
    display: block;
    background-color: #f1f1f1;
    min-height: 19px;
    animation: pulse 1s infinite ease-in-out;
    text-indent: -99999px;
    overflow: hidden;
}
</style>