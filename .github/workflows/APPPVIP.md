Tuyệt vời\! Yêu cầu của bạn là hoàn toàn hợp lý để dễ dàng triển khai. Dưới đây là \*\*toàn bộ bộ mã nguồn hoàn chỉnh\*\* cho \*\*Product Analytics Dashboard\*\* của NexiFy Hub, sẵn sàng để bạn sao chép và dán vào dự án React/Vite của mình.

Bộ mã nguồn này tích hợp tất cả các yêu cầu đã thảo luận: TypeScript, React Hooks, Tailwind CSS, React Query, Axios, Recharts, xử lý loading/error/empty states, và mock data với độ trễ.

\---

\#\#\# \*\*BỘ MÃ NGUỒN HOÀN CHỈNH: DASHBOARD PHÂN TÍCH SẢN PHẨM CỦA NEXIFY HUB\*\*

Bạn có thể tạo một dự án Vite mới và sau đó sao chép các file vào đúng vị trí của chúng.

\#\#\#\# \*\*1. Cấu trúc thư mục dự kiến:\*\*

\`\`\`  
my-product-analytics/  
├── public/  
│ └── index.html  
├── src/  
│ ├── api/  
│ │ └── productAnalyticsService.ts  
│ ├── components/  
│ │ ├── ui/  
│ │ │ └── Card.tsx  
│ │ ├── common/  
│ │ │ ├── DateRangePicker.tsx  
│ │ │ ├── ErrorMessage.tsx  
│ │ │ └── Spinner.tsx  
│ │ └── productAnalytics/  
│ │ ├── DailyActiveUsersChart.tsx  
│ │ ├── FeatureUsageTable.tsx  
│ │ ├── ProductAnalyticsDashboard.tsx  
│ │ └── ProductTypeFilter.tsx  
│ ├── data/  
│ │ └── mockProductAnalyticsData.ts  
│ ├── hooks/  
│ │ └── useProductAnalyticsData.ts  
│ ├── types/  
│ │ └── productAnalytics.ts  
│ ├── App.tsx  
│ ├── main.tsx  
│ └── index.css  
├── .gitignore  
├── package.json  
├── tailwind.config.js  
└── tsconfig.json  
\`\`\`

\#\#\#\# \*\*2. Hướng dẫn cài đặt và chạy:\*\*

1\.  \*\*Khởi tạo dự án Vite (nếu chưa có):\*\*  
    \`\`\`bash  
    npm create vite@latest my-product-analytics \--template react-ts  
    cd my-product-analytics  
    \`\`\`

2\.  \*\*Cài đặt Tailwind CSS:\*\*  
    \`\`\`bash  
    npm install \-D tailwindcss postcss autoprefixer  
    npx tailwindcss init \-p  
    \`\`\`

3\.  \*\*Cài đặt các thư viện cần thiết:\*\*  
    \`\`\`bash  
    npm install axios @tanstack/react-query recharts date-fns  
    npm install \-D @tanstack/react-query-devtools \# (Tùy chọn, cho devtools)  
    \`\`\`

4\.  \*\*Tạo các thư mục:\*\*  
    Tạo tất cả các thư mục con trong \`src/\` theo cấu trúc đã mô tả ở trên.

5\.  \*\*Sao chép mã nguồn:\*\*  
    Sao chép nội dung của từng file dưới đây và dán vào đúng vị trí file tương ứng trong dự án của bạn.

6\.  \*\*Chạy dự án:\*\*  
    \`\`\`bash  
    npm run dev  
    \`\`\`  
    Mở trình duyệt tại địa chỉ được hiển thị trong terminal (thường là \`http://localhost:5173/\`).

\---

\#\#\#\# \*\*3. Mã nguồn từng file:\*\*

\*\*\`package.json\` (Ví dụ, hãy đảm bảo các dependencies được cài đặt)\*\*

\`\`\`json  
{  
  "name": "my-product-analytics",  
  "private": true,  
  "version": "0.0.0",  
  "type": "module",  
  "scripts": {  
    "dev": "vite",  
    "build": "tsc && vite build",  
    "lint": "eslint . \--ext ts,tsx \--report-unused-disable-directives \--max-warnings 0",  
    "preview": "vite preview"  
  },  
  "dependencies": {  
    "@tanstack/react-query": "^5.45.1",  
    "axios": "^1.7.2",  
    "date-fns": "^3.6.0",  
    "react": "^18.3.1",  
    "react-dom": "^18.3.1",  
    "recharts": "^2.12.7"  
  },  
  "devDependencies": {  
    "@tanstack/react-query-devtools": "^5.45.1",  
    "@types/react": "^18.3.3",  
    "@types/react-dom": "^18.3.0",  
    "@types/recharts": "^1.8.29",  
    "@typescript-eslint/eslint-plugin": "^7.13.1",  
    "@typescript-eslint/parser": "^7.13.1",  
    "@vitejs/plugin-react": "^4.3.1",  
    "autoprefixer": "^10.4.19",  
    "eslint": "^8.57.0",  
    "eslint-plugin-react-hooks": "^4.6.2",  
    "eslint-plugin-react-refresh": "^0.4.7",  
    "postcss": "^8.4.38",  
    "tailwindcss": "^3.4.4",  
    "typescript": "^5.2.2",  
    "vite": "^5.3.1"  
  }  
}  
\`\`\`

\*\*\`tailwind.config.js\`\*\*

\`\`\`javascript  
/\*\* @type {import('tailwindcss').Config} \*/  
export default {  
  content: \[  
    "./index.html",  
    "./src/\*\*/\*.{js,ts,jsx,tsx}",  
  \],  
  theme: {  
    extend: {  
      colors: {  
        // Define NexiFy brand colors and system colors for consistency  
        nexifyPrimary: '\#5A31F4', // Tím NexiFy  
        nexifyAccent: '\#FF7A00', // Cam Năng động  
        successGreen: '\#4CAF50', // Xanh lá cây cho thành công  
        errorRed: '\#F44336',     // Đỏ cho lỗi  
        infoYellow: '\#FFC107',   // Vàng cho thông tin/cảnh báo  
        // Grayscale palette for text, backgrounds, borders  
        grayLight: '\#f3f4f6',  
        grayDefault: '\#6b7280',  
        grayDark: '\#1f2937',  
      },  
      fontFamily: {  
        // Define custom fonts, e.g., 'Inter' as per Design System  
        sans: \['Inter', 'sans-serif'\],  
      }  
    },  
  },  
  plugins: \[\],  
}  
\`\`\`

\*\*\`src/index.css\`\*\*

\`\`\`css  
/\* src/index.css \*/  
@tailwind base;  
@tailwind components;  
@tailwind utilities;

/\* Import Inter font from Google Fonts \*/  
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700\&display=swap');

body {  
  font-family: 'Inter', sans-serif;  
  \-webkit-font-smoothing: antialiased;  
  \-moz-osx-font-smoothing: grayscale;  
  background-color: \#f8fafc; /\* A light background for the page, as per UI/UX \*/  
  color: \#1f2937; /\* Default text color (grayDark) \*/  
}  
\`\`\`

\*\*\`src/main.tsx\`\*\*

\`\`\`typescript  
// src/main.tsx  
import React from 'react';  
import ReactDOM from 'react-dom/client';  
import App from './App';  
import './index.css'; // Import global Tailwind CSS and custom styles

ReactDOM.createRoot(document.getElementById('root')\!).render(  
  \<React.StrictMode\>  
    \<App /\>  
  \</React.StrictMode\>  
);  
\`\`\`

\*\*\`src/App.tsx\`\*\*

\`\`\`typescript  
// src/App.tsx  
// Điểm khởi đầu của ứng dụng, thiết lập React Query và render Product Analytics Dashboard.

import React from 'react';  
import {  
  QueryClient,  
  QueryClientProvider,  
} from '@tanstack/react-query';  
// Optional: Import React Query Devtools for visual debugging in development  
import { ReactQueryDevtools } from '@tanstack/react-query-devtools';

import ProductAnalyticsDashboard from './components/productAnalytics/ProductAnalyticsDashboard'; // Import dashboard chính

// Tạo một instance của QueryClient  
// Đây là nơi bạn có thể cấu hình các tùy chọn toàn cục cho React Query.  
// Nó sẽ quản lý cache, fetching, và các trạng thái của queries trong toàn bộ ứng dụng.  
const queryClient \= new QueryClient({  
  defaultOptions: {  
    queries: {  
      // Cấu hình mặc định cho tất cả các queries. Ví dụ:  
      // Thử lại queries 3 lần khi gặp lỗi mạng.  
      retry: 3,  
      // \`refetchOnWindowFocus: false\` có thể hữu ích trong môi trường dev  
      // để tránh spam request khi chuyển tab, hoặc nếu bạn muốn kiểm soát rõ ràng hơn.  
      // refetchOnWindowFocus: false,  
    },  
  },  
});

const App: React.FC \= () \=\> {  
  return (  
    // Bọc toàn bộ ứng dụng trong QueryClientProvider để các component con có thể sử dụng React Query.  
    // Bất kỳ component nào được render bên trong Provider này đều có thể truy cập context của React Query.  
    \<QueryClientProvider client={queryClient}\>  
      \<div className="App"\>  
        {/\* Render component Dashboard Phân tích Sản phẩm chính \*/}  
        \<ProductAnalyticsDashboard /\>  
      \</div\>

      {/\* Optional: React Query Devtools cho việc debug trực quan các queries trong môi trường phát triển. \*/}  
      {/\* Để sử dụng, hãy đảm bảo bạn đã cài đặt: \`npm install \-D @tanstack/react-query-devtools\` \*/}  
      {/\* Chỉ hiển thị trong môi trường dev để tối ưu hiệu suất. \*/}  
      {process.env.NODE\_ENV \=== 'development' && \<ReactQueryDevtools initialIsOpen={false} /\>}  
    \</QueryClientProvider\>  
  );  
};

export default App;  
\`\`\`

\*\*\`src/types/productAnalytics.ts\`\*\*

\`\`\`typescript  
// src/types/productAnalytics.ts  
// Định nghĩa các TypeScript interfaces để mô tả cấu trúc dữ liệu cho Product Analytics.

/\*\*  
 \* Đại diện cho một điểm dữ liệu sử dụng sản phẩm hàng ngày.  
 \*/  
export interface ProductUsageDataPoint {  
  date: string; // Định dạng: yyyy-mm-dd  
  dailyActiveUsers: number;  
  newUsers: number;  
  churnedUsers: number; // Số lượng người dùng đã ngừng sử dụng sản phẩm  
}

/\*\*  
 \* Đại diện cho dữ liệu sử dụng của một tính năng cụ thể.  
 \*/  
export interface FeatureUsageData {  
  featureName: string;  
  usageCount: number; // Tổng số lần sử dụng tính năng  
  usersCount: number; // Số lượng người dùng đã sử dụng tính năng này  
  averageSessionDuration: number; // Thời lượng phiên trung bình khi sử dụng tính năng này, tính bằng phút  
}

/\*\*  
 \* Đại diện cho dữ liệu tổng quan.  
 \*/  
export interface ProductAnalyticsSummary {  
  totalActiveUsers: number;  
  totalFeaturesUsed: number;  
  averageSessionDurationAcrossAllProducts: number; // Thời lượng phiên trung bình trên tất cả sản phẩm, tính bằng phút  
}

/\*\*  
 \* Kết hợp các kiểu dữ liệu trên thành một phản hồi API hoàn chỉnh.  
 \*/  
export interface ProductAnalyticsResponse {  
  summary: ProductAnalyticsSummary;  
  productUsageOverTime: ProductUsageDataPoint\[\];  
  featureUsage: FeatureUsageData\[\];  
}  
\`\`\`

\*\*\`src/data/mockProductAnalyticsData.ts\`\*\*

\`\`\`typescript  
// src/data/mockProductAnalyticsData.ts  
// Tạo một object mockProductAnalyticsData tuân thủ ProductAnalyticsResponse với dữ liệu giả lập có ý nghĩa.

import { ProductAnalyticsResponse, ProductUsageDataPoint, FeatureUsageData } from '../types/productAnalytics';  
import { format, subDays, addDays } from 'date-fns';

/\*\*  
 \* Hàm helper để tạo dữ liệu sử dụng sản phẩm theo thời gian.  
 \* Mô phỏng xu hướng tăng/giảm nhẹ để tạo dữ liệu chân thực hơn.  
 \* @param startDate Ngày bắt đầu để tạo dữ liệu.  
 \* @param numDays Số ngày cần tạo dữ liệu.  
 \* @returns Mảng các ProductUsageDataPoint.  
 \*/  
const generateProductUsageData \= (  
  startDate: Date,  
  numDays: number  
): ProductUsageDataPoint\[\] \=\> {  
  const data: ProductUsageDataPoint\[\] \= \[\];  
  let baseActiveUsers \= 50000; // Người dùng hoạt động ban đầu  
  let baseNewUsers \= 1000;  
  let baseChurnedUsers \= 500;

  for (let i \= 0; i \< numDays; i++) {  
    const currentDate \= addDays(startDate, i);  
    const dateString \= format(currentDate, 'yyyy-MM-dd');

    // Tạo biến động nhẹ để mô phỏng dữ liệu thực tế  
    baseActiveUsers \= Math.max(  
      45000, // Đảm bảo số người dùng hoạt động tối thiểu  
      Math.min(  
        60000, // Đảm bảo số người dùng hoạt động tối đa  
        baseActiveUsers \+ Math.floor(Math.random() \* 500\) \- 200 // Biến động \+/- 200 người dùng hàng ngày  
      )  
    );

    baseNewUsers \= Math.max(  
      500,  
      Math.min(  
        1500,  
        baseNewUsers \+ Math.floor(Math.random() \* 100\) \- 40  
      )  
    );  
    // Số người dùng rời bỏ thường là một phần nhỏ của người dùng hoạt động  
    baseChurnedUsers \= Math.min(  
      baseActiveUsers \* 0.02, // Không quá 2% người dùng hoạt động  
      Math.max(  
        200,  
        baseChurnedUsers \+ Math.floor(Math.random() \* 50\) \- 20  
      )  
    );

    data.push({  
      date: dateString,  
      dailyActiveUsers: baseActiveUsers,  
      newUsers: baseNewUsers,  
      churnedUsers: baseChurnedUsers,  
    });  
  }  
  return data;  
};

// Định nghĩa ngày bắt đầu cho dữ liệu giả lập (30 ngày trước ngày 2025-06-04)  
const startDate \= subDays(new Date('2025-06-04'), 29); // Bắt đầu từ ngày 2025-05-06

// Tạo dữ liệu sử dụng sản phẩm trong 30 ngày  
const mockProductUsageOverTime \= generateProductUsageData(startDate, 30);

/\*\*  
 \* Hàm helper để tạo dữ liệu sử dụng tính năng.  
 \* @returns Mảng các FeatureUsageData.  
 \*/  
const generateFeatureUsageData \= (): FeatureUsageData\[\] \=\> {  
  return \[  
    {  
      featureName: 'Báo cáo doanh thu',  
      usageCount: 12500,  
      usersCount: 850,  
      averageSessionDuration: 7.2,  
    },  
    {  
      featureName: 'Quản lý kho hàng',  
      usageCount: 9800,  
      usersCount: 720,  
      averageSessionDuration: 5.8,  
    },  
    {  
      featureName: 'Phân tích hành vi khách hàng',  
      usageCount: 6300,  
      usersCount: 510,  
      averageSessionDuration: 10.5,  
    },  
    {  
      featureName: 'Tạo chiến dịch Marketing',  
      usageCount: 4100,  
      usersCount: 390,  
      averageSessionDuration: 6.1,  
    },  
    {  
      featureName: 'Dashboard tổng quan',  
      usageCount: 15000,  
      usersCount: 950,  
      averageSessionDuration: 3.1,  
    },  
    {  
        featureName: 'Quản lý Đơn hàng',  
        usageCount: 22000,  
        usersCount: 1100,  
        averageSessionDuration: 4.5,  
    },  
  \];  
};

/\*\*  
 \* Đối tượng dữ liệu giả lập hoàn chỉnh cho Product Analytics Dashboard.  
 \* Tuân thủ interface ProductAnalyticsResponse.  
 \*/  
export const mockProductAnalyticsData: ProductAnalyticsResponse \= {  
  summary: {  
    // Các giá trị này có thể là tổng hợp từ dữ liệu sử dụng hoặc các con số đại diện  
    totalActiveUsers: 55000, // Ví dụ tổng số người dùng hoạt động trong giai đoạn  
    totalFeaturesUsed: 6,    // Ví dụ tổng số tính năng riêng biệt được sử dụng  
    averageSessionDurationAcrossAllProducts: 6.5, // Ví dụ thời lượng phiên trung bình tổng thể tính bằng phút  
  },  
  productUsageOverTime: mockProductUsageOverTime, // Dữ liệu 30 ngày  
  featureUsage: generateFeatureUsageData(), // Dữ liệu sử dụng tính năng  
};  
\`\`\`

\*\*\`src/api/productAnalyticsService.ts\`\*\*

\`\`\`typescript  
// src/api/productAnalyticsService.ts  
// Service API để lấy dữ liệu phân tích sản phẩm, hỗ trợ mock data trong môi trường phát triển.

import axios from 'axios';  
import { ProductAnalyticsResponse } from '../types/productAnalytics'; // Import kiểu dữ liệu phản hồi  
import { mockProductAnalyticsData } from '../data/mockProductAnalyticsData'; // Import dữ liệu giả lập

// URL cơ sở cho API backend của bạn.  
// Đây sẽ là URL của API Gateway của bạn cho Product Analytics Microservice.  
// Ví dụ: 'http://localhost:8080/api/v1' nếu API Gateway của bạn chạy trên cổng 8080\.  
const BASE\_URL \= 'http://localhost:8000/api'; // \*Điều chỉnh BASE\_URL này theo URL API Gateway/Backend thực tế của bạn\*

/\*\*  
 \* Lấy dữ liệu phân tích sản phẩm từ API.  
 \* Trong môi trường phát triển, nó trả về dữ liệu giả lập với độ trễ mô phỏng 500ms.  
 \* Trong môi trường production, nó thực hiện một cuộc gọi API Axios thực sự.  
 \*  
 \* @param startDate \- Ngày bắt đầu cho phạm vi dữ liệu (định dạng: yyyy-mm-dd).  
 \* @param endDate \- Ngày kết thúc cho phạm vi dữ liệu (định dạng: yyyy-mm-dd).  
 \* @param productType \- (Tùy chọn) Chuỗi bộ lọc loại sản phẩm.  
 \* @returns Một Promise phân giải thành ProductAnalyticsResponse.  
 \*/  
export const getProductAnalyticsData \= async (  
  startDate: string,  
  endDate: string,  
  productType?: string // Bộ lọc loại sản phẩm tùy chọn  
): Promise\<ProductAnalyticsResponse\> \=\> {  
  // Kiểm tra nếu đang chạy trong môi trường phát triển  
  if (process.env.NODE\_ENV \=== 'development') {  
    // Mô phỏng độ trễ API (500ms theo yêu cầu) để có trải nghiệm tải chân thực trong quá trình phát triển.  
    return new Promise((resolve) \=\> {  
      setTimeout(() \=\> {  
        console.log('\[Dev Mode\] Đang trả về dữ liệu giả lập cho phân tích sản phẩm...');  
        resolve(mockProductAnalyticsData); // Trả về dữ liệu giả lập đã định nghĩa trước  
      }, 500); // 500ms delay  
    });  
  } else {  
    // Trong môi trường production hoặc các môi trường khác, thực hiện một cuộc gọi API thực sự.  
    try {  
      // Axios tự động xử lý các tham số truy vấn từ đối tượng \`params\`.  
      const response \= await axios.get\<ProductAnalyticsResponse\>(  
        \`${BASE\_URL}/product-analytics/data\`, // Điểm cuối API backend thực tế của bạn  
        {  
          params: { // Tham số truy vấn cho yêu cầu API  
            startDate,   // Ví dụ: ?startDate=2025-05-06  
            endDate,     // Ví dụ: \&endDate=2025-06-04  
            productType, // Ví dụ: \&productType=Product%20A (sẽ bị bỏ qua nếu undefined)  
          },  
        }  
      );  
      return response.data; // Trả về dữ liệu nhận được từ backend  
    } catch (error) {  
      console.error('Lỗi khi lấy dữ liệu phân tích sản phẩm từ API thực:', error);  
      // Ném lại lỗi với thông báo thân thiện với người dùng để hook/component gọi nó có thể bắt.  
      throw new Error(  
        (error as any).response?.data?.message || 'Đã xảy ra lỗi không mong muốn khi lấy dữ liệu phân tích.'  
      );  
    }  
  }  
};  
\`\`\`

\*\*\`src/hooks/useProductAnalyticsData.ts\`\*\*

\`\`\`typescript  
// src/hooks/useProductAnalyticsData.ts  
// Custom hook để lấy dữ liệu phân tích sản phẩm bằng React Query.

import { useQuery } from '@tanstack/react-query';  
import { getProductAnalyticsData } from '../api/productAnalyticsService'; // Import hàm dịch vụ API  
import { ProductAnalyticsResponse } from '../types/productAnalytics'; // Import kiểu dữ liệu phản hồi

/\*\*  
 \* Custom hook để lấy dữ liệu phân tích sản phẩm bằng \`@tanstack/react-query\`.  
 \* Hook này trừu tượng hóa logic lấy dữ liệu và cung cấp cách thuận tiện để  
 \* truy cập các trạng thái loading, error và data trong các component React của bạn.  
 \*  
 \* @param startDate \- Ngày bắt đầu cho phạm vi dữ liệu (yyyy-mm-dd).  
 \* @param endDate \- Ngày kết thúc cho phạm vi dữ liệu (yyyy-mm-dd).  
 \* @param productType \- (Tùy chọn) Chuỗi bộ lọc loại sản phẩm.  
 \* @returns Một đối tượng chứa \`data\`, \`isLoading\`, \`isError\`, và \`error\` từ \`useQuery\`.  
 \*/  
export const useProductAnalyticsData \= (  
  startDate: string,  
  endDate: string,  
  productType?: string  
) \=\> {  
  // \`useQuery\` hook nhận một đối tượng cấu hình.  
  return useQuery\<ProductAnalyticsResponse, Error\>({  
    // \`queryKey\`: Một mảng duy nhất gồm các chuỗi và đối tượng có thể tuần tự hóa.  
    // TanStack Query sử dụng key này để cache kết quả truy vấn và tìm nạp lại dữ liệu  
    // khi bất kỳ phần nào của key thay đổi. Điều này làm cho truy vấn tự động  
    // phản ứng với các thay đổi trong \`startDate\`, \`endDate\`, hoặc \`productType\`.  
    queryKey: \['productAnalyticsData', startDate, endDate, productType\],

    // \`queryFn\`: Hàm bất đồng bộ thực sự lấy dữ liệu.  
    // Hàm này nên trả về một Promise phân giải với dữ liệu.  
    queryFn: () \=\> getProductAnalyticsData(startDate, endDate, productType),

    // \`staleTime\`: Khoảng thời gian tính bằng mili giây mà dữ liệu vẫn được coi là "mới" (fresh).  
    // Dữ liệu mới sẽ không kích hoạt việc tìm nạp lại khi component mount hoặc cửa sổ focus.  
    // Sau \`staleTime\`, dữ liệu trở thành "cũ" (stale) và sẽ được tìm nạp lại (nếu được yêu cầu).  
    staleTime: 5 \* 60 \* 1000, // 5 phút (theo yêu cầu: 5 \* 60 \* 1000 mili giây)

    // \`gcTime\` (Garbage Collection Time): Khoảng thời gian tính bằng mili giây mà  
    // các truy vấn không hoạt động (không còn được quan sát bởi bất kỳ component nào) vẫn còn trong cache.  
    // Sau \`gcTime\`, dữ liệu sẽ được thu gom rác khỏi bộ nhớ.  
    gcTime: 10 \* 60 \* 1000, // 10 phút (theo yêu cầu: 10 \* 60 \* 1000 mili giây)

    // \`enabled\`: Một boolean xác định liệu truy vấn có nên chạy hay không.  
    // Đặt \`enabled\` thành \`false\` ngăn truy vấn chạy nếu  
    // \`startDate\` hoặc \`endDate\` không hợp lệ/không được cung cấp, tránh các cuộc gọi API không cần thiết.  
    enabled: \!\!startDate && \!\!endDate, // Đảm bảo cả hai ngày đều là chuỗi không rỗng  
  });  
};  
\`\`\`

\*\*\`src/components/ui/Card.tsx\`\*\*

\`\`\`typescript  
// src/components/ui/Card.tsx  
import React from 'react';

/\*\*  
 \* Props cho Card component.  
 \* @param children \- Nội dung bên trong card.  
 \* @param className \- Các Tailwind CSS classes tùy chỉnh.  
 \*/  
interface CardProps {  
  children: React.ReactNode; // Nội dung bên trong card  
  className?: string;       // Các Tailwind CSS classes bổ sung  
}

/\*\*  
 \* Một component Card có thể tái sử dụng cho các phần UI nhất quán.  
 \* Cung cấp nền trắng, bo góc, đổ bóng và padding.  
 \*/  
const Card: React.FC\<CardProps\> \= ({ children, className }) \=\> {  
  return (  
    \<div  
      className={\`bg-white p-6 rounded-lg shadow-sm border border-gray-200 ${className || ''}\`}  
    \>  
      {children}  
    \</div\>  
  );  
};

export default Card;  
\`\`\`

\*\*\`src/components/common/DateRangePicker.tsx\`\*\*

\`\`\`typescript  
// src/components/common/DateRangePicker.tsx  
// Component cho phép chọn khoảng ngày bắt đầu và kết thúc sử dụng input type="date".

import React, { useState, useEffect } from 'react';  
// Import date-fns để xử lý và so sánh ngày tháng một cách mạnh mẽ hơn  
import { format, parseISO, isAfter, isBefore } from 'date-fns';

/\*\*  
 \* Props cho DateRangePicker component.  
 \* @param startDate \- Ngày bắt đầu hiện tại được chọn (định dạng yyyy-MM-dd).  
 \* @param endDate \- Ngày kết thúc hiện tại được chọn (định dạng yyyy-MM-dd).  
 \* @param onDateRangeChange \- Callback function được gọi khi khoảng ngày thay đổi.  
 \* @param className \- (Tùy chọn) Các Tailwind CSS classes bổ sung cho container.  
 \*/  
interface DateRangePickerProps {  
  startDate: string;  
  endDate: string;  
  onDateRangeChange: (start: string, end: string) \=\> void;  
  className?: string;  
}

/\*\*  
 \* Một component đơn giản cho phép người dùng chọn khoảng ngày bằng cách sử dụng input date HTML gốc.  
 \* Nó đảm bảo ngày kết thúc không đứng trước ngày bắt đầu bằng cách tự động điều chỉnh.  
 \*/  
const DateRangePicker: React.FC\<DateRangePickerProps\> \= ({  
  startDate,  
  endDate,  
  onDateRangeChange,  
  className \= '',  
}) \=\> {  
  // State nội bộ để quản lý giá trị của input, được đồng bộ với props.  
  // Sử dụng \`startDate\` và \`endDate\` từ props trực tiếp đảm bảo kiểm soát từ bên ngoài.  
  const \[currentStartDate, setCurrentStartDate\] \= useState\<string\>(startDate);  
  const \[currentEndDate, setCurrentEndDate\] \= useState\<string\>(endDate);

  // Đồng bộ state nội bộ với props bên ngoài. Điều này rất quan trọng nếu component cha  
  // có thể cập nhật \`startDate\` hoặc \`endDate\` một cách độc lập (ví dụ: reset bộ lọc).  
  // useEffect này ngăn chặn state cũ nếu component cha cập nhật ngày.  
  useEffect(() \=\> {  
    setCurrentStartDate(startDate);  
    setCurrentEndDate(endDate);  
  }, \[startDate, endDate\]);

  const handleStartDateChange \= (e: React.ChangeEvent\<HTMLInputElement\>) \=\> {  
    const newStart \= e.target.value;  
    const newStartParsed \= parseISO(newStart); // Phân tích chuỗi thành đối tượng Date để so sánh  
    const currentEndParsed \= parseISO(currentEndDate);

    setCurrentStartDate(newStart);

    // Nếu ngày bắt đầu mới sau ngày kết thúc hiện tại,  
    // tự động đặt ngày kết thúc thành ngày bắt đầu mới để duy trì khoảng ngày hợp lệ.  
    if (isAfter(newStartParsed, currentEndParsed)) {  
      setCurrentEndDate(newStart);  
      onDateRangeChange(newStart, newStart); // Gọi callback với khoảng ngày đã điều chỉnh  
    } else {  
      onDateRangeChange(newStart, currentEndDate); // Gọi callback với ngày đã chọn  
    }  
  };

  const handleEndDateChange \= (e: React.ChangeEvent\<HTMLInputElement\>) \=\> {  
    const newEnd \= e.target.value;  
    const newEndParsed \= parseISO(newEnd); // Phân tích chuỗi thành đối tượng Date để so sánh  
    const currentStartParsed \= parseISO(currentStartDate);

    setCurrentEndDate(newEnd);

    // Nếu ngày kết thúc mới trước ngày bắt đầu hiện tại,  
    // tự động đặt ngày bắt đầu thành ngày kết thúc mới để duy trì khoảng ngày hợp lệ.  
    if (isBefore(newEndParsed, currentStartParsed)) {  
      setCurrentStartDate(newEnd);  
      onDateRangeChange(newEnd, newEnd); // Gọi callback với khoảng ngày đã điều chỉnh  
    } else {  
      onDateRangeChange(currentStartDate, newEnd); // Gọi callback với ngày đã chọn  
    }  
  };

  return (  
    \<div className={\`flex flex-col sm:flex-row items-center space-y-2 sm:space-y-0 sm:space-x-4 ${className}\`}\>  
      \<div className="flex items-center space-x-2"\>  
        \<label htmlFor="startDate" className="text-gray-700 font-medium"\>Từ:\</label\>  
        \<input  
          type="date"  
          id="startDate"  
          value={currentStartDate}  
          onChange={handleStartDateChange}  
          // Các class Tailwind để tạo kiểu  
          className="p-2 border border-gray-300 rounded-md focus:ring-nexifyPrimary focus:border-nexifyPrimary outline-none text-gray-700"  
        /\>  
      \</div\>  
      \<div className="flex items-center space-x-2"\>  
        \<label htmlFor="endDate" className="text-gray-700 font-medium"\>Đến:\</label\>  
        \<input  
          type="date"  
          id="endDate"  
          value={currentEndDate}  
          onChange={handleEndDateChange}  
          // Các class Tailwind để tạo kiểu  
          className="p-2 border border-gray-300 rounded-md focus:ring-nexifyPrimary focus:border-nexifyPrimary outline-none text-gray-700"  
        /\>  
      \</div\>  
    \</div\>  
  );  
};

export default DateRangePicker;  
\`\`\`

\*\*\`src/components/common/Spinner.tsx\`\*\*

\`\`\`typescript  
// src/components/common/Spinner.tsx  
// Component hiển thị một spinner loading đơn giản.

import React from 'react';

/\*\*  
 \* Props cho Spinner component.  
 \* @param size \- Điều khiển kích thước được định nghĩa trước của spinner ('sm', 'md', 'lg'). Mặc định là 'md'.  
 \* @param className \- Các Tailwind CSS classes tùy chọn để áp dụng cho spinner.  
 \*/  
interface SpinnerProps {  
  size?: 'sm' | 'md' | 'lg'; // Điều khiển kích thước của spinner  
  className?: string;       // Các Tailwind CSS classes bổ sung  
}

/\*\*  
 \* Một component spinner loading động đơn giản sử dụng Tailwind CSS.  
 \* Cung cấp phản hồi trực quan rằng nội dung đang được tải.  
 \* Nó sử dụng màu NexiFy Primary để nhất quán với hệ thống thiết kế.  
 \*/  
const Spinner: React.FC\<SpinnerProps\> \= ({ size \= 'md', className \= '' }) \=\> {  
  // Xác định các class kích thước dựa trên prop 'size'.  
  // Chúng ta cũng điều chỉnh độ rộng viền một chút cho spinner nhỏ hơn/lớn hơn để có vẻ ngoài tốt hơn.  
  const spinnerSize \=  
    size \=== 'sm' ? 'w-4 h-4 border-2' : size \=== 'lg' ? 'w-8 h-8 border-4' : 'w-6 h-6 border-\[3px\]'; // border-\[3px\] là độ dày tùy chỉnh cho 'md'

  return (  
    \<div  
      className={\`  
        animate-spin rounded-full border-solid border-current border-r-transparent   
        ${spinnerSize} text-nexifyPrimary ${className} // Sử dụng màu nexifyPrimary từ tailwind.config.js  
      \`}  
      role="status" // Role truy cập cho trình đọc màn hình  
      aria-label="Đang tải" // Nhãn truy cập  
    \>  
      \<span className="sr-only"\>Đang tải...\</span\> {/\* Văn bản chỉ dành cho trình đọc màn hình \*/}  
    \</div\>  
  );  
};

export default Spinner;  
\`\`\`

\*\*\`src/components/common/ErrorMessage.tsx\`\*\*

\`\`\`typescript  
// src/components/common/ErrorMessage.tsx  
// Component hiển thị thông báo lỗi thân thiện với người dùng.

import React from 'react';

/\*\*  
 \* Props cho ErrorMessage component.  
 \* @param message \- Thông báo lỗi cần hiển thị.  
 \* @param className \- Các Tailwind CSS classes tùy chỉnh cho container.  
 \*/  
interface ErrorMessageProps {  
  message: string;  
  className?: string; // Các Tailwind CSS classes bổ sung cho container  
}

/\*\*  
 \* Một component để hiển thị thông báo lỗi thân thiện với người dùng.  
 \* Được tạo kiểu với nền/chữ màu đỏ để hiển thị rõ ràng.  
 \*/  
const ErrorMessage: React.FC\<ErrorMessageProps\> \= ({ message, className \= '' }) \=\> {  
  return (  
    \<div  
      className={\`p-4 bg-errorRed/10 border border-errorRed text-errorRed-700 rounded-md ${className}\`}  
      role="alert" // Role truy cập  
    \>  
      \<div className="flex items-center"\>  
        {/\* Error Icon (sử dụng SVG đơn giản) \*/}  
        \<svg  
          className="h-5 w-5 text-errorRed mr-2"  
          fill="currentColor"  
          viewBox="0 0 20 20"  
          xmlns="http://www.w3.org/2000/svg"  
        \>  
          \<path  
            fillRule="evenodd"  
            d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7 4a1 1 0 11-2 0 1 1 0 012 0zm-1-9a1 1 0 00-1 1v4a1 1 0 102 0V6a1 1 0 00-1-1z"  
            clipRule="evenodd"  
          /\>  
        \</svg\>  
        \<p className="font-semibold"\>Lỗi:\</p\>  
      \</div\>  
      \<p className="mt-1 text-sm"\>{message}\</p\>  
    \</div\>  
  );  
};

export default ErrorMessage;  
\`\`\`

\*\*\`src/components/productAnalytics/ProductTypeFilter.tsx\`\*\*

\`\`\`typescript  
// src/components/productAnalytics/ProductTypeFilter.tsx

import React from 'react';

/\*\*  
 \* Props cho ProductTypeFilter component.  
 \* @param onSelect \- Callback function được gọi khi người dùng chọn một loại sản phẩm.  
 \*                   Truyền vào giá trị mới được chọn (chuỗi rỗng cho 'Tất cả sản phẩm').  
 \* @param selectedType \- Loại sản phẩm hiện tại đang được chọn (chuỗi rỗng cho 'Tất cả sản phẩm').  
 \*/  
interface ProductTypeFilterProps {  
  onSelect: (productType: string) \=\> void;  
  selectedType: string;  
}

/\*\*  
 \* Một component dropdown (select) để lọc dữ liệu phân tích theo loại sản phẩm cụ thể.  
 \* Được tạo kiểu bằng Tailwind CSS và ánh xạ tùy chọn 'Tất cả sản phẩm' thành giá trị chuỗi rỗng.  
 \*/  
const ProductTypeFilter: React.FC\<ProductTypeFilterProps\> \= ({  
  onSelect,  
  selectedType,  
}) \=\> {  
  // Danh sách loại sản phẩm giả định. Trong ứng dụng thực tế, điều này có thể đến từ một cuộc gọi API  
  // đến một dịch vụ backend cung cấp các danh mục hoặc loại sản phẩm có sẵn.  
  const productTypes \= \['Tất cả sản phẩm', 'Sản phẩm A', 'Sản phẩm B', 'Sản phẩm C'\];

  const handleChange \= (event: React.ChangeEvent\<HTMLSelectElement\>) \=\> {  
    onSelect(event.target.value); // Gọi callback của component cha với giá trị mới  
  };

  return (  
    \<div className="flex items-center gap-2"\> {/\* Sử dụng flexbox và gap để tạo khoảng cách \*/}  
      \<label htmlFor="productType" className="text-gray-700 text-sm font-medium sr-only md:not-sr-only"\>  
        {/\* sr-only để ẩn nhãn trên màn hình nhỏ (chỉ dành cho trình đọc màn hình), not-sr-only cho màn hình lớn hơn \*/}  
        Loại sản phẩm:  
      \</label\>  
      \<select  
        id="productType"  
        // Áp dụng các class Tailwind CSS để tạo kiểu nhất quán  
        className="p-2 border border-gray-300 rounded-md shadow-sm   
                   focus:outline-none focus:ring-2 focus:ring-nexifyPrimary focus:border-transparent   
                   w-full sm:w-auto text-gray-700 bg-white"  
        value={selectedType}  
        onChange={handleChange}  
        aria-label="Lọc theo loại sản phẩm" // Thực hành truy cập tốt nhất  
      \>  
        {productTypes.map((type) \=\> (  
          \<option  
            key={type}  
            // Ánh xạ văn bản 'Tất cả sản phẩm' thành giá trị chuỗi rỗng.  
            // Đây là một mẫu phổ biến cho lựa chọn "không có bộ lọc" trong API.  
            value={type \=== 'Tất cả sản phẩm' ? '' : type}  
          \>  
            {type}  
          \</option\>  
        ))}  
      \</select\>  
    \</div\>  
  );  
};

export default ProductTypeFilter;  
\`\`\`

\*\*\`src/components/productAnalytics/FeatureUsageTable.tsx\`\*\*

\`\`\`typescript  
// src/components/productAnalytics/FeatureUsageTable.tsx

import React from 'react';  
import { FeatureUsageData } from '../../types/productAnalytics'; // Import kiểu dữ liệu

interface FeatureUsageTableProps {  
  data: FeatureUsageData\[\]; // Mảng dữ liệu sử dụng tính năng  
}

/\*\*  
 \* Hiển thị một bảng sạch sẽ và dễ đọc hiển thị số liệu thống kê sử dụng tính năng.  
 \* Áp dụng Tailwind CSS để tạo kiểu, xử lý trạng thái dữ liệu trống và định dạng số để dễ đọc.  
 \*/  
const FeatureUsageTable: React.FC\<FeatureUsageTableProps\> \= ({ data }) \=\> {  
  // Xử lý trường hợp không có dữ liệu hoặc dữ liệu trống  
  if (\!data || data.length \=== 0\) {  
    return (  
      \<div className="flex items-center justify-center h-full text-gray-500 min-h-\[150px\] bg-gray-50 rounded-lg"\>  
        \<p\>Không có dữ liệu sử dụng tính năng cho giai đoạn đã chọn.\</p\>  
      \</div\>  
    );  
  }

  return (  
    // Cho phép bảng cuộn ngang trên màn hình nhỏ nếu nội dung tràn ra  
    \<div className="overflow-x-auto"\>  
      \<table className="min-w-full bg-white border border-gray-200 rounded-lg shadow-sm"\>  
        \<thead className="bg-gray-50"\> {/\* Sử dụng nền màu xám nhạt cho tiêu đề bảng \*/}  
          \<tr\>  
            \<th className="py-3 px-4 text-left text-xs font-medium text-gray-600 uppercase tracking-wider border-b border-gray-200"\>  
              Tên tính năng  
            \</th\>  
            \<th className="py-3 px-4 text-left text-xs font-medium text-gray-600 uppercase tracking-wider border-b border-gray-200"\>  
              Số lượng sử dụng  
            \</th\>  
            \<th className="py-3 px-4 text-left text-xs font-medium text-gray-600 uppercase tracking-wider border-b border-gray-200"\>  
              Số lượng người dùng  
            \</th\>  
            \<th className="py-3 px-4 text-left text-xs font-medium text-gray-600 uppercase tracking-wider border-b border-gray-200"\>  
              Thời lượng phiên TB (phút)  
            \</th\>  
          \</tr\>  
        \</thead\>  
        \<tbody className="divide-y divide-gray-100"\> {/\* Thêm đường phân cách giữa các hàng \*/}  
          {data.map((item) \=\> (  
            \<tr key={item.featureName} className="hover:bg-gray-50 transition-colors duration-150"\> {/\* Hiệu ứng hover mượt mà \*/}  
              \<td className="py-3 px-4 whitespace-nowrap text-sm text-gray-800"\>  
                {item.featureName}  
              \</td\>  
              \<td className="py-3 px-4 whitespace-nowrap text-sm text-gray-700"\>  
                {item.usageCount.toLocaleString()} {/\* Định dạng số với dấu phẩy để dễ đọc \*/}  
              \</td\>  
              \<td className="py-3 px-4 whitespace-nowrap text-sm text-gray-700"\>  
                {item.usersCount.toLocaleString()} {/\* Định dạng số với dấu phẩy để dễ đọc \*/}  
              \</td\>  
              \<td className="py-3 px-4 whitespace-nowrap text-sm text-gray-700"\>  
                {item.averageSessionDuration.toFixed(1)} {/\* Một chữ số thập phân cho thời lượng \*/}  
              \</td\>  
            \</tr\>  
          ))}  
        \</tbody\>  
      \</table\>  
    \</div\>  
  );  
};

export default FeatureUsageTable;  
\`\`\`

\*\*\`src/components/productAnalytics/DailyActiveUsersChart.tsx\`\*\*

\`\`\`typescript  
// src/components/productAnalytics/DailyActiveUsersChart.tsx

import React from 'react';  
import {  
  LineChart,  
  Line,  
  XAxis,  
  YAxis,  
  CartesianGrid,  
  Tooltip,  
  Legend,  
  ResponsiveContainer, // Để biểu đồ responsive  
} from 'recharts';  
import { ProductUsageDataPoint } from '../../types/productAnalytics'; // Import kiểu dữ liệu  
import { format, parseISO } from 'date-fns'; // Để định dạng và phân tích ngày tháng

interface DailyActiveUsersChartProps {  
  data: ProductUsageDataPoint\[\]; // Mảng điểm dữ liệu sử dụng hàng ngày  
}

/\*\*  
 \* Hiển thị biểu đồ đường về người dùng hoạt động hàng ngày, người dùng mới và người dùng rời bỏ theo thời gian.  
 \* Sử dụng thư viện Recharts cho khả năng biểu đồ phong phú.  
 \* Xử lý trạng thái dữ liệu trống một cách duyên dáng và áp dụng màu sắc của hệ thống thiết kế NexiFy Hub.  
 \*/  
const DailyActiveUsersChart: React.FC\<DailyActiveUsersChartProps\> \= ({ data }) \=\> {  
  // Xử lý trường hợp không có dữ liệu hoặc dữ liệu trống  
  if (\!data || data.length \=== 0\) {  
    return (  
      \<div className="flex items-center justify-center h-full text-gray-500 min-h-\[300px\] bg-gray-50 rounded-lg"\>  
        \<p\>Không có dữ liệu người dùng hoạt động hàng ngày cho giai đoạn đã chọn.\</p\>  
      \</div\>  
    );  
  }

  // Hàm định dạng cho các dấu tick trên trục X (chuỗi ngày)  
  // Chuyển đổi 'yyyy-MM-dd' sang định dạng dễ đọc hơn như 'Thg 6 01'  
  const dateFormatter \= (tick: string) \=\> {  
    // parseISO xử lý chuỗi 'yyyy-MM-dd' chính xác  
    const date \= parseISO(tick);  
    return format(date, 'MMM dd'); // Ví dụ: 'Thg 6 01'  
  };

  // Nội dung Tooltip tùy chỉnh để hiển thị chi tiết hơn khi di chuột  
  // Component này nhận các props \`active\`, \`payload\`, \`label\` từ Recharts Tooltip  
  const CustomTooltip \= ({ active, payload, label }: any) \=\> {  
    if (active && payload && payload.length) {  
      // Định dạng nhãn ngày cho tiêu đề tooltip  
      const dateLabel \= format(parseISO(label), 'EEEE, MMMM dd, yyyy'); // Ví dụ: 'Thứ Hai, Tháng 6 01, 2025'  
      return (  
        \<div className="p-3 bg-white border border-gray-200 rounded-md shadow-lg text-sm"\>  
          \<p className="font-semibold text-gray-800 mb-1"\>{dateLabel}\</p\>  
          {payload.map((entry: any, index: number) \=\> (  
            \<p key={\`item-${index}\`} style={{ color: entry.color }}\>  
              {/\* Hiển thị tên và giá trị, định dạng giá trị với toLocaleString cho dấu phẩy \*/}  
              {\`${entry.name}: \`}  
              \<span className="font-bold"\>{entry.value.toLocaleString()}\</span\>  
            \</p\>  
          ))}  
        \</div\>  
      );  
    }  
    return null;  
  };

  return (  
    // ResponsiveContainer làm cho biểu đồ tự điều chỉnh kích thước theo chiều rộng và chiều cao của container cha  
    \<ResponsiveContainer width="100%" height={400}\> {/\* Chiều cao tăng lên để hiển thị tốt hơn \*/}  
      \<LineChart  
        data={data}  
        margin={{  
          top: 15,    // Lề trên cho biểu đồ  
          right: 30,  // Lề phải  
          left: 20,   // Lề trái  
          bottom: 5,  // Lề dưới  
        }}  
      \>  
        {/\* Đường lưới cho dễ đọc hơn \*/}  
        \<CartesianGrid strokeDasharray="3 3" stroke="\#e0e0e0" /\> {/\* Lưới gạch ngang màu xám nhạt \*/}

        {/\* Trục X cho ngày tháng \*/}  
        \<XAxis  
          dataKey="date"  
          tickFormatter={dateFormatter} // Sử dụng hàm định dạng tùy chỉnh cho ngày tháng  
          tick={{ fill: '\#6b7280', fontSize: 12 }} // Màu xám 500 của Tailwind cho nhãn dấu tick  
          tickLine={false} // Ẩn đường dấu tick  
          axisLine={{ stroke: '\#e0e0e0' }} // Màu đường trục  
          minTickGap={20} // Khoảng cách tối thiểu giữa các dấu tick để tránh chồng chéo, đặc biệt trên màn hình nhỏ  
        /\>

        {/\* Trục Y cho số lượng người dùng \*/}  
        \<YAxis  
          tickFormatter={(value) \=\> value.toLocaleString()} // Định dạng số với dấu phẩy  
          tick={{ fill: '\#6b7280', fontSize: 12 }}  
          tickLine={false}  
          axisLine={{ stroke: '\#e0e0e0' }}  
          // Tùy chọn, thêm miền để ngăn các đường chạm vào cạnh trên/dưới,  
          // và đảm bảo trục Y bắt đầu gần với dataMin nhưng không nhất thiết là 0 cho các xu hướng.  
          domain={\['dataMin \- 500', (dataMax: number) \=\> Math.round(dataMax \* 1.1)\]} // Thêm một số khoảng đệm vào phía trên trục Y, và đảm bảo cơ sở hơi dưới data min  
        /\>

        {/\* Tooltip khi di chuột, sử dụng component tùy chỉnh của chúng ta \*/}  
        \<Tooltip content={\<CustomTooltip /\>} /\>

        {/\* Chú giải cho các đường biểu đồ \*/}  
        \<Legend wrapperStyle={{ paddingTop: '15px', fontSize: 14 }} /\> {/\* Thêm padding phía trên chú giải, điều chỉnh cỡ chữ \*/}

        {/\* Các đường cho mỗi điểm dữ liệu \- sử dụng màu sắc của hệ thống thiết kế NexiFy \*/}  
        \<Line  
          type="monotone" // Đường cong mượt mà  
          dataKey="dailyActiveUsers"  
          stroke="\#5A31F4" // Màu chính của NexiFy cho Người dùng hoạt động hàng ngày  
          strokeWidth={2} // Độ dày đường  
          activeDot={{ r: 6 }} // Dấu chấm lớn hơn khi di chuột để tương tác  
          name="Người dùng hoạt động" // Nhãn cho chú giải và tooltip  
          dot={false} // Ẩn các điểm dữ liệu riêng lẻ (chấm) trên đường để có chế độ xem xu hướng sạch hơn  
        /\>  
        \<Line  
          type="monotone"  
          dataKey="newUsers"  
          stroke="\#FF7A00" // Màu nhấn của NexiFy cho Người dùng mới  
          strokeWidth={2}  
          activeDot={{ r: 6 }}  
          name="Người dùng mới"  
          dot={false}  
        /\>  
        \<Line  
          type="monotone"  
          dataKey="churnedUsers"  
          stroke="\#EF4444" // Màu đỏ tương đương với red-500 của Tailwind cho người dùng rời bỏ (errorRed, hoặc tương tự)  
          strokeWidth={2}  
          activeDot={{ r: 6 }}  
          name="Người dùng rời bỏ"  
          dot={false}  
        /\>  
      \</LineChart\>  
    \</ResponsiveContainer\>  
  );  
};

export default DailyActiveUsersChart;  
\`\`\`

\*\*\`src/components/productAnalytics/ProductAnalyticsDashboard.tsx\`\*\*

\`\`\`typescript  
// src/components/productAnalytics/ProductAnalyticsDashboard.tsx  
// Component chính cho Product Analytics Dashboard, tổng hợp các bộ lọc, biểu đồ, bảng và dữ liệu tổng quan.

import React, { useState } from 'react';  
import { subDays, format } from 'date-fns'; // Để xử lý và định dạng ngày tháng

// Import các hooks và types  
import { useProductAnalyticsData } from '../../hooks/useProductAnalyticsData';

// Import các component dùng chung  
import DateRangePicker from '../common/DateRangePicker';  
import Spinner from '../common/Spinner'; // Component spinner loading  
import ErrorMessage from '../common/ErrorMessage'; // Component hiển thị lỗi  
import Card from '../ui/Card'; // Component Card cơ bản

// Import các component chuyên biệt cho phân tích sản phẩm  
import DailyActiveUsersChart from './DailyActiveUsersChart'; // Biểu đồ xu hướng người dùng hàng ngày  
import FeatureUsageTable from './FeatureUsageTable'; // Bảng phân tích sử dụng tính năng  
import ProductTypeFilter from './ProductTypeFilter'; // Bộ lọc dropdown theo loại sản phẩm

/\*\*  
 \* Component dashboard chính cho Phân tích Sản phẩm.  
 \* Điều phối việc lấy dữ liệu dựa trên các bộ lọc do người dùng chọn (khoảng ngày, loại sản phẩm)  
 \* và hiển thị dữ liệu đã lấy bằng cách sử dụng các component con khác nhau.  
 \* Xử lý các trạng thái loading, error và dữ liệu trống một cách duyên dáng.  
 \*/  
const ProductAnalyticsDashboard: React.FC \= () \=\> {  
  // State: Khởi tạo ngày bắt đầu (29 ngày trước để có đủ 30 ngày bao gồm cả ngày hiện tại)  
  const \[startDate, setStartDate\] \= useState\<string\>(format(subDays(new Date(), 29), 'yyyy-MM-dd'));  
  // State: Ngày kết thúc là ngày hiện tại  
  const \[endDate, setEndDate\] \= useState\<string\>(format(new Date(), 'yyyy-MM-dd'));

  // State: Quản lý loại sản phẩm được chọn. Chuỗi rỗng \`''\` tương ứng với "Tất cả sản phẩm"  
  const \[selectedProductType, setSelectedProductType\] \= useState\<string\>('');

  // Sử dụng custom hook của React Query để lấy dữ liệu.  
  // \`data\` sẽ chứa dữ liệu \`ProductAnalyticsResponse\` khi thành công.  
  // \`isLoading\` là true ban đầu và trong quá trình tìm nạp dữ liệu lần đầu.  
  // \`isFetching\` là true bất cứ khi nào dữ liệu đang được tìm nạp (bao gồm cả tìm nạp lại trong nền).  
  // \`isError\` là true nếu truy vấn gặp lỗi.  
  // \`error\` chứa đối tượng Error nếu \`isError\` là true.  
  const { data, isLoading, isError, error, isFetching } \= useProductAnalyticsData(  
    startDate,  
    endDate,  
    selectedProductType // \`selectedProductType\` rỗng sẽ được xử lý thành \`undefined\` trong API service  
  );

  /\*\*  
   \* Hàm xử lý để cập nhật khoảng ngày được chọn.  
   \* Việc này sẽ kích hoạt việc tìm nạp lại dữ liệu bởi hook \`useProductAnalyticsData\`.  
   \* @param start Chuỗi ngày bắt đầu mới (yyyy-mm-dd).  
   \* @param end Chuỗi ngày kết thúc mới (yyyy-mm-dd).  
   \*/  
  const handleDateRangeChange \= (start: string, end: string) \=\> {  
    setStartDate(start);  
    setEndDate(end);  
  };

  /\*\*  
   \* Hàm xử lý để cập nhật bộ lọc loại sản phẩm được chọn.  
   \* Việc này cũng sẽ kích hoạt việc tìm nạp lại dữ liệu.  
   \* @param type Chuỗi loại sản phẩm mới được chọn.  
   \*/  
  const handleProductTypeSelect \= (type: string) \=\> {  
    setSelectedProductType(type);  
  };

  // Xác định xem nội dung có đang tải tích cực (tải lần đầu hoặc tải lại trong nền) hay không.  
  const isContentLoading \= isLoading || isFetching;

  // \--- Conditional Rendering cho Trạng thái tải ban đầu / Lỗi \---  
  // Hiển thị Spinner toàn màn hình chỉ khi đang tải lần đầu (isLoading)  
  if (isLoading) {  
    return (  
      \<div className="flex flex-col justify-center items-center h-screen bg-gray-100"\>  
        \<Spinner size="lg" className="text-nexifyPrimary" /\> {/\* Sử dụng spinner lớn với màu chính của NexiFy \*/}  
        \<p className="ml-3 text-gray-700 mt-4 text-lg"\>Đang tải dữ liệu phân tích...\</p\>  
      \</div\>  
    );  
  }

  // Hiển thị ErrorMessage toàn màn hình nếu có lỗi (chủ yếu là lỗi ban đầu hoặc lỗi nghiêm trọng)  
  if (isError) {  
    return (  
      \<div className="flex flex-col justify-center items-center h-screen bg-gray-100"\>  
        \<ErrorMessage  
          message={error?.message || 'Không thể tải dữ liệu. Vui lòng kiểm tra kết nối mạng và thử lại.'}  
          className="max-w-xl text-center"  
        /\>  
      \</div\>  
    );  
  }

  // Nếu dữ liệu được tìm nạp thành công nhưng rỗng (không có productUsageOverTime hoặc featureUsage)  
  const hasNoData \= \!data || (data.productUsageOverTime.length \=== 0 && data.featureUsage.length \=== 0);

  if (hasNoData) {  
    return (  
      \<div className="p-4 sm:p-8 bg-gray-100 min-h-screen flex justify-center items-center"\>  
        \<div className="bg-white p-6 rounded-lg shadow-sm border border-gray-200 text-gray-500 text-lg text-center max-w-xl"\>  
          \<p\>Không tìm thấy dữ liệu phân tích nào cho giai đoạn và bộ lọc đã chọn.\</p\>  
          \<p className="mt-2 text-sm"\>Vui lòng thử điều chỉnh phạm vi ngày hoặc loại sản phẩm.\</p\>  
        \</div\>  
      \</div\>  
    );  
  }

  // \--- Nội dung Dashboard chính \---  
  // Dữ liệu (\`data\`) đã chắc chắn tồn tại ở đây vì các điều kiện \`isLoading\` và \`isError\` đã được xử lý.  
  const summary \= data.summary; // Lấy dữ liệu tóm tắt từ phản hồi

  return (  
    // Main container cho dashboard, với padding, nền xám nhạt và font Inter  
    \<div className="p-4 sm:p-6 bg-gray-100 min-h-screen font-sans text-gray-800 relative"\>  
      {/\* Overlay spinner cho việc tìm nạp lại dữ liệu trong nền (\`isFetching\`) \*/}  
      {isFetching && (  
        \<div className="absolute inset-0 bg-white bg-opacity-75 flex flex-col justify-center items-center z-10 rounded-lg"\>  
          \<Spinner size="lg" className="text-nexifyPrimary" /\>  
          \<p className="ml-3 text-gray-700 mt-4 text-lg"\>Đang cập nhật dữ liệu...\</p\>  
        \</div\>  
      )}

      \<h1 className="text-3xl font-bold mb-6 text-center sm:text-left"\>  
        Dashboard Phân tích Sản phẩm  
      \</h1\>

      {/\* Phần Bộ lọc: Chứa DateRangePicker và ProductTypeFilter \*/}  
      \<div className="bg-white p-4 rounded-lg shadow-sm border border-gray-200 mb-6 flex flex-col md:flex-row gap-4 justify-between items-center"\>  
        \<DateRangePicker  
          startDate={startDate}  
          endDate={endDate}  
          onDateRangeChange={handleDateRangeChange}  
        /\>  
        \<ProductTypeFilter  
          selectedType={selectedProductType}  
          onSelect={handleProductTypeSelect}  
        /\>  
      \</div\>

      {/\* Phần Thẻ tóm tắt: Hiển thị các chỉ số hiệu suất chính \*/}  
      \<div className="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8"\>  
        \<Card className="flex flex-col items-center justify-center p-6 text-center"\>  
          \<p className="text-sm font-semibold text-gray-600 mb-2"\>Tổng người dùng hoạt động\</p\>  
          \<p className="text-4xl font-bold text-nexifyPrimary"\>  
            {summary.totalActiveUsers.toLocaleString()} {/\* Định dạng số với dấu phẩy \*/}  
          \</p\>  
          \<p className="text-sm text-gray-500 mt-1"\>  
            (Người dùng duy nhất trong giai đoạn)  
          \</p\>  
        \</Card\>  
        \<Card className="flex flex-col items-center justify-center p-6 text-center"\>  
          \<p className="text-sm font-semibold text-gray-600 mb-2"\>Tổng số tính năng đã sử dụng\</p\>  
          \<p className="text-4xl font-bold text-nexifyPrimary"\>  
            {summary.totalFeaturesUsed.toLocaleString()}  
          \</p\>  
          \<p className="text-sm text-gray-500 mt-1"\>  
            (Tính năng độc đáo có hoạt động)  
          \</p\>  
        \</Card\>  
        \<Card className="flex flex-col items-center justify-center p-6 text-center"\>  
          \<p className="text-sm font-semibold text-gray-600 mb-2"\>Thời lượng phiên trung bình\</p\>  
          \<p className="text-4xl font-bold text-nexifyPrimary"\>  
            {summary.averageSessionDurationAcrossAllProducts.toFixed(1)}{' '}phút  
          \</p\>  
          \<p className="text-sm text-gray-500 mt-1"\>  
            (Trên tất cả các tương tác sản phẩm)  
          \</p\>  
        \</Card\>  
      \</div\>

      {/\* Phần Biểu đồ và Bảng dữ liệu \*/}  
      \<div className="grid grid-cols-1 lg:grid-cols-2 gap-6"\>  
        {/\* Biểu đồ người dùng hoạt động hàng ngày \*/}  
        \<Card\>  
          \<h2 className="text-xl font-semibold text-gray-800 mb-4"\>Xu hướng sử dụng hàng ngày\</h2\>  
          \<DailyActiveUsersChart data={data.productUsageOverTime} /\>  
        \</Card\>

        {/\* Bảng sử dụng tính năng \*/}  
        \<Card\>  
          \<h2 className="text-xl font-semibold text-gray-800 mb-4"\>Phân tích chi tiết sử dụng tính năng\</h2\>  
          \<FeatureUsageTable data={data.featureUsage} /\>  
        \</Card\>  
      \</div\>  
    \</div\>  
  );  
};

export default ProductAnalyticsDashboard;  
\`\`\`

