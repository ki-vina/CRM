# CRM (ki-vina/CRM): bản fork Twenty theo giao diện VKX

Fork của [twentyhq/twenty](https://github.com/twentyhq/twenty) (AGPL-3.0, xem `LICENSE`). Đây là bản fork,
không phải sản phẩm chính thức của Twenty. Nhánh làm việc: `kivina/vkx-ui`, tách từ tag `twenty/v2.64.1`.
`main` của fork chỉ đồng bộ với upstream.

## Đã đổi (chỉ màu + logo)
- `packages/twenty-ui/design-tokens/color/gray.ts`: thang xám đổi sang navy VKX (nền `#0a1120`, chữ `#e9f0fa`; sáng: nền trắng, chữ navy).
- `.../color/blue.ts`: thang "blue" (nút chính, liên kết, hàng chọn, focus) đổi sang vàng `#f7c41c`. Nhãn/tag xanh dương cũng thành vàng.
- `.../font.ts`: chữ trên nút nhấn `#05090f`.
- `packages/twenty-ui/src/theme/*`: file sinh tự động từ token (`npx tsx scripts/generateThemeTokens.ts`).
- `packages/twenty-front/public/images/icons/**`: toàn bộ 112 icon thay bằng logo VKX (kể cả logo mặc định ở trang đăng nhập).
- `packages/twenty-front/index.html`, `public/manifest.json`: tên "VKX CRM", theme-color. `DefaultWorkspaceLogo.ts`: logo mặc định lấy từ chính server.

## Build và kiểm tra
```
corepack-free: node .yarn/releases/yarn-4.18.1.cjs workspaces focus twenty-monorepo twenty-front twenty-front-component-renderer twenty-ui twenty-shared twenty-sdk twenty-client-sdk
npx tsx packages/twenty-ui/scripts/generateThemeTokens.ts --check
npx nx build twenty-front          # cần `yarn` trong PATH
```
Image: `packages/twenty-docker/twenty/Dockerfile` (build bằng docker trên máy build, tag riêng, vd `kivina-twenty:vkx-<ngày>`).

## Nâng cấp Twenty
`git fetch upstream --tags && git checkout -b kivina/vkx-ui-<ver> twenty/v<ver> && git cherry-pick <các commit VKX>`,
rồi chạy lại `generateThemeTokens.ts` (xung đột thường chỉ ở các file sinh tự động: xóa và sinh lại).

## Giấy phép
AGPL-3.0: mã bản sửa nằm trong repo này. Không đụng file `@license Enterprise`. Không dùng tên/logo Twenty làm thương hiệu.
